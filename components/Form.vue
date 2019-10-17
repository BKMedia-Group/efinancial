<template>
  <form
    id="app"
    @submit.prevent="submit()"
    action="https://vuejs.org/"
    method="post"
    novalidate="true"
  >
    <div :class="{ error: validation.hasError('firstName') }">
      <input
        id="firstName"
        v-model="firstName"
        type="text"
        name="firstName"
        placeholder="First Name*"
      />
      <div class="message">{{ validation.firstError('firstName') }}</div>
      <input
        id="lastName"
        v-model="lastName"
        type="text"
        name="lastName"
        placeholder="Last Name*"
        required
      />
    </div>
    <div>
      <select id="gender" v-model="gender" name="gender" required>
        <option diabled value="">Select Gender*</option>
        <option>Vanilla Sky</option>
        <option>Atomic Blonde</option>
      </select>
      <input
        id="dob"
        v-model="dob"
        type="text"
        name="dob"
        placeholder="DOB: MM/DD/YYYY*"
        required
      />
    </div>
    <div>
      <div :class="{ error: validation.hasError('email') }">
        <input
          id="email"
          v-model="email"
          type="email"
          name="email"
          placeholder="Email Address*"
        />
        <div class="message">{{ validation.firstError('email') }}</div>
      </div>
      <div>
        <input
          id="phone"
          v-model="phone"
          type="tel"
          name="phone"
          placeholder="Phone Number"
        />
      </div>
    </div>
    <div>
      <input
        id="cc_number"
        v-model="cc_number"
        type="text"
        name="cc_number"
        placeholder="Credit Card Number"
      />
      <input
        id="exp_date"
        v-model="exp_date"
        type="text"
        name="exp_date"
        placeholder="MM/YY"
      />
      <input id="cvv" v-model="cvv" type="text" name="cvv" placeholder="CVV" />
    </div>
    <div class="form_image_required">
      <img src="~assets/images/cards.svg" alt="" />
      <span>
        * Denote required fields
      </span>
    </div>
    <div>
      <label>
        <input
          id="checkbox1"
          type="checkbox"
          name="activate"
          value=""
          v-model="activate"
        />
        By clicking this box I authorize the Program Administrator to hereby
        activate my Wellness Benefit Program. I understand that my Wellness
        Benefit monthly membership fee will be debited automatically each month
        from my credit card for as long as I remain a member. I understand that
        I will be automatically enrolled in the Family Program. I understand I
        am providing the information on this form directly to the Program
        Administrator to activate my membership. I also authorize Wellness
        Benefits to arrange monthly debits of the $19.95 membership fee from my
        credit card for remittance to the Program Administrator until I cancel
        by calling the toll-free customer service at 1-800-878-3733. The
        Wellness Benefit Program is not insurance.
      </label>
      <label>
        <input
          id="checkbox2"
          type="checkbox"
          name="membership"
          value=""
          v-model="membership"
        />
        By clicking on the button, I agree to start my membership and pay the
        membership fee each month that I remain a member, and that clicking is
        my electronic signature accepting the programs
        <a href="#" @click.prevent="isVisible1 = true">
          Terms and Conditions
        </a>
        , achknowledging receipt of the
        <a href="#" @click.prevent="isVisible2 = true">
          Program Privacy Policy
        </a>
        and agreeing to the same.
      </label>
    </div>
    <div>
      <input type="submit" value="Submit" />
    </div>
  </form>
</template>
<script>
import SimpleVueValidation from 'simple-vue-validator'
const Validator = SimpleVueValidation.Validator
export default {
  data() {
    return {
      firstName: '',
      lastName: '',
      gender: '',
      dob: '',
      email: '',
      phone: '',
      cc_number: '',
      cvv: ''
    }
  },
  methods: {
    submit() {
      this.$validate().then((success) => {
        if (success) {
          alert('success')
        }
      })
    }
  },
  validators: {
    email: (value) => {
      return Validator.value(value)
        .required()
        .email()
    },
    firstName: (value) => {
      return Validator.value(value).required()
    }
  }
}
</script>
