<template>
  <Layout class="l_contact_container">
    <h1 class="l_title">Say hi!</h1>
    <p>Leave me a note with any questions you might have, I'll get back to you as soon as possible.</p>
    <form name="sentMessage" id="contactForm" novalidate >
      <div class="control-group">
        <div class="form-group floating-label-form-group controls">
          <label>Name</label>
          <input type="text" class="form-control" v-model="contact.name" id="name" required data-validation-required-message="Please enter your name.">
          <p class="help-block text-danger"></p>
        </div>
      </div>
      <div class="control-group">
        <div class="form-group floating-label-form-group controls">
          <label>Email Address</label>
          <input type="email" class="form-control" v-model="contact.email" id="email" required data-validation-required-message="Please enter your email address.">
          <p class="help-block text-danger"></p>
        </div>
      </div>
      <div class="control-group">
        <div class="form-group col-xs-12 floating-label-form-group controls">
          <label>Phone Number</label>
          <input type="tel" class="form-control" v-model="contact.phone" id="phone" required data-validation-required-message="Please enter your phone number.">
          <p class="help-block text-danger"></p>
        </div>
      </div>
      <div class="control-group">
        <div class="form-group floating-label-form-group controls">
          <label>Message</label>
          <textarea rows="5" class="form-control" v-model="contact.message" id="message" required data-validation-required-message="Please enter a message."></textarea>
          <p class="help-block text-danger"></p>
        </div>
      </div>
      <br>
      <div id="success"></div>
      <button type="submit" class="btn btn-primary" id="sendMessageButton" @click.prevent="onSubmit">Send</button>
    </form>
  </Layout>
</template>

<script>
import axios from 'axios'
export default {
  name: 'ContactPage',
  data(){
    return{
      contact:{
        name: '',
        email: '',
        phone: '',
        message:''
      }
    }
  },
  methods:{
    async onSubmit(){
      if(!this.contact.name) return window.alert('Name is required')
      if(!this.contact.email) return window.alert('Email is required')
      if(!this.contact.phone) return window.alert('Phone is required')
      try {
       const { data } = await axios({
          method: 'POST',
          url: `${this.GRIDSOME_API_URL}/contacts`,
          data: this.contact
        })
      } catch (error) {
        console.log(error.message);
        window.alert('提交失败，请稍后重试')
      }
    }
  }
}
</script>
<style scoped lang='scss'>
.l_contact_container{
  max-width: 860px;
  .l_title{
    margin-bottom: 40px;
  }
  #contactForm{
    margin-top: 20px;
    width: 570px;
    .control-group{
      .form-group{
        label{
          display: block;
          font-size: 16px;
          color: #666;
        }
        .form-control{
          border: none;
          outline: none;
          border-bottom: 1px solid #eee;
          width: 100%;
          line-height: 16px;
          padding: 8px;
        }
      }
    }
    .btn-primary{
      padding: 8px 20px;
      border: none;
      outline: none;
      cursor: pointer;
      border-radius: 2px;
      background-color: #000;
      color: #fff;
      font-size: 14px;
      // background-color: #fff;
    }
  }
}
</style>
