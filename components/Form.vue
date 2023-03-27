<script>
import emailjs from '@emailjs/browser';
import { settings } from '~~/settings/settings';

const {YOUR_SERVICE_ID, YOUR_TEMPLATE_ID, YOUR_PUBLIC_KEY} = settings;

export default {
  data() {
    return {
      name_input: null,
      name_error: null,
      email_input: null,
      email_error: null,
      phone_input: null,
      phone_error: null,
      message_input: null,
      message_error: null
    }
  },
  methods: {
    validate_name() {
      if (this.$refs.form.name.value == '') {
        this.name_error = 'Пустое поле!';
        return false;
      } 
      else if (this.$refs.form.name.value.length > 50) {
        this.name_error = 'Не более 50 символов!';
        return false;
      } 
      else {
        this.name_error = null;
        return true;
      }
    },
    validate_email() {
      if (this.$refs.form.email.value == '') {
        this.email_error = 'Пустое поле!';
        return false;
      } 
      else if (this.$refs.form.email.value.match(/^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/g) == null) {
        this.email_error = 'Неверный адрес почты!';
        return false;
      } 
      else {
        this.email_error = null;
        return true;
      }
    },
    validate_phone() {
      if (this.$refs.form.phone.value != '' && this.$refs.form.phone.value.match(/^\+\d+$/g) == null) {
        this.phone_error = 'Неверный номер телефона!';
        return false;
      }
      else {
        this.phone_error = null;
        return true;
      }
    },
    validate_message() {
      if (this.$refs.form.message.value > 180) {
        this.message_error = 'Не более 180 символов!';
        return false;
      } 
      else {
        this.message_error = null;
        return true;
      }
    },
    sendEmail() {
      if (this.validate_name() && this.validate_email() && this.validate_phone() && this.validate_message()) {
        emailjs.sendForm(YOUR_SERVICE_ID, YOUR_TEMPLATE_ID, this.$refs.form, YOUR_PUBLIC_KEY)
          .then(() => {
            this.name_input = null;
            this.email_input = null;
            this.phone_input = null;
            this.message_input = null;
          })
      } 
      else {
        return;
      }
    }
  }
}
</script>

<template>
  <form ref="form" @submit.prevent="sendEmail">
    <div class="input-wrap">
      <input 
        id="name" 
        class="input"
        name="name"
        type="text" 
        v-model="name_input">
      <label 
        for="name" 
        :class="{ 'label-active': name_input ? true : false }">
          Имя*
      </label>
      <small>{{ name_error }}</small>
    </div>
    <div class="input-wrap">
      <input 
        id="email" 
        class="input" 
        name="email"
        type="text"
        v-model="email_input">
      <label 
        for="email"
        :class="{ 'label-active': email_input ? true : false }">
          Email*
      </label>
      <small>{{ email_error }}</small>
    </div>
    <div class="input-wrap">
      <input 
        id="phone" 
        class="input" 
        name="phone"
        type="text"
        v-model="phone_input">
      <label 
        for="phone"
        :class="{ 'label-active': phone_input ? true : false }">
          Телефон*
      </label>
      <small>{{ phone_error }}</small>
    </div>
    <div id="message-wrap">
      <textarea 
        id="message" 
        class="textarea" 
        name="message"
        placeholder="Сообщение" 
        rows="6"
        v-model="message_input">
      </textarea>
      <small>{{ message_error }}</small>
    </div>
    <input 
      id="submit-btn" 
      type="submit" 
      value="Отправить">
  </form>
</template>

<style scoped>
form {
  box-sizing: border-box;
  width: 100%;
  max-width: 625px;
}

.input-wrap, #message-wrap {
  position: relative;
  padding-bottom: 24px;
}

.input, .textarea {
  width: 100%;
  box-sizing: border-box;
  border: 1px solid rgb(226, 226, 226);
  border-radius: 4px;
  font-family: OpenSans Regular, sans-serif;
  font-size: 16px;
  font-weight: 400;
  color: rgb(71, 71, 71);
}

.input:focus, .textarea:focus {
  border-color: rgb(71, 71, 71);
  outline: none;
}

.input {
  padding: 23px 16px 7px;
}

.textarea {
  padding: 16px;
}

label {
  position: absolute;
  top: 16.5px;
  left: 16px;
  transition: all 0.15s ease 0s;
  font-family: OpenSans Regular, sans-serif;
  font-size: 16px;
  font-weight: 400;
  color: rgb(71, 71, 71);
}

.input-wrap:focus-within label, .label-active {
  top: 6px;
  font-size: 12px;
  color: rgb(171, 100, 60);
}

small {
  margin: 0;
  font-family: OpenSans Regular, sans-serif;
  font-size: 12px;
  font-weight: 400;
  color: rgb(239, 0, 0);
}

#submit-btn {
  width: 100%;
  box-sizing: border-box;
  margin-bottom: 24px;
  border: none;
  border-radius: 4px;
  padding: 8px 32px;
  background-color: rgb(230, 148, 101);
  font-family: OpenSans Bold, sans-serif;
  font-size: 14px;
  font-weight: 700;
  line-height: 40px;
  text-transform: uppercase;
  text-align: center;
  color: rgb(0, 0, 0);
}

#submit-btn:hover {
  background-color: rgb(236, 183, 160);
}
</style>