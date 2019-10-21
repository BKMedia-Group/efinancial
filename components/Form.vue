<template>
  <div>
    <form novalidate @submit.prevent="submit()">
      <div class="form-row">
        <div class="col">
          <div
            class="input"
            :class="{ error: validation.hasError('data.Person.FirstName') }"
          >
            <input
              v-model="data.Person.FirstName"
              type="text"
              placeholder="First Name*"
            />
            <div class="message">
              {{ validation.firstError('data.Person.FirstName') }}
            </div>
          </div>
        </div>
        <div class="col">
          <div
            class="input"
            :class="{ error: validation.hasError('data.Person.LastName') }"
          >
            <input
              v-model="data.Person.LastName"
              type="text"
              placeholder="Last Name*"
            />
            <div class="message">
              {{ validation.firstError('data.Person.LastName') }}
            </div>
          </div>
        </div>
      </div>
      <div class="form-row">
        <div class="col">
          <div
            class="input"
            :class="{ error: validation.hasError('data.Address.Address1') }"
          >
            <input
              v-model="data.Address.Address1"
              type="text"
              placeholder="Address*"
            />
            <div class="message">
              {{ validation.firstError('data.Address.Address1') }}
            </div>
          </div>
        </div>
        <div class="col">
          <div
            class="input"
            :class="{ error: validation.hasError('data.Address.City') }"
          >
            <input
              v-model="data.Address.City"
              type="text"
              placeholder="City*"
            />
            <div class="message">
              {{ validation.firstError('data.Address.City') }}
            </div>
          </div>
        </div>
      </div>
      <div class="form-row">
        <div class="col">
          <div
            class="input"
            :class="{ error: validation.hasError('data.Address.PostalCode') }"
          >
            <input
              v-model="data.Address.PostalCode"
              type="text"
              placeholder="PostalCode*"
            />
            <div class="message">
              {{ validation.firstError('data.Address.PostalCode') }}
            </div>
          </div>
        </div>
        <div class="col">
          <div
            class="input"
            :class="{ error: validation.hasError('data.Address.State') }"
          >
            <input
              v-model="data.Address.State"
              type="text"
              placeholder="Last Name*"
            />
            <div class="message">
              {{ validation.firstError('data.Address.State') }}
            </div>
          </div>
        </div>
      </div>
      <div class="form-row">
        <div class="col">
          <div
            class="input"
            :class="{ error: validation.hasError('data.Person.Gender') }"
          >
            <select v-model="data.Person.Gender">
              <option diabled value="">Select Person.Gender*</option>
              <option>Male</option>
              <option>Female</option>
            </select>
            <div class="message">
              {{ validation.firstError('data.Person.Gender') }}
            </div>
          </div>
        </div>
        <div class="col">
          <div
            class="input"
            :class="{ error: validation.hasError('data.Person.DateOfBirth') }"
          >
            <cleave
              v-model="data.Person.DateOfBirth"
              placeholder="Date Of Birth: MM/DD/YYYY*"
              :options="{
                date: true,
                datePatter: ['m', 'd', 'Y'],
                delimiter: '/'
              }"
            ></cleave>
            <div class="message">
              {{ validation.firstError('data.Person.DateOfBirth') }}
            </div>
          </div>
        </div>
      </div>
      <div class="form-row">
        <div class="col">
          <div
            class="input"
            :class="{ error: validation.hasError('data.Person.Email') }"
          >
            <input
              v-model="data.Person.Email"
              type="Email"
              placeholder="Email Address*"
            />
            <div class="message">
              {{ validation.firstError('data.Person.Email') }}
            </div>
          </div>
        </div>
        <div class="col">
          <div class="input">
            <cleave
              v-model="data.Person.PhoneNumber"
              :options="{ phone: true, phoneRegionCode: 'us', delimiter: '-' }"
              placeholder="Phone Number"
            ></cleave>
          </div>
        </div>
      </div>
      <div class="input cc">
        <div class="input" id="cc_number">
          <cleave
            v-model="data.Billing.AccountNumber"
            :options="ccOptions"
            placeholder="Credit Card Number"
          ></cleave>
        </div>
        <div class="input" id="exp_date">
          <cleave
            v-model="data.exp_date"
            :options="{ date: true, datePattern: ['m', 'y'] }"
            placeholder="MM/YY"
          ></cleave>
        </div>
      </div>
      <div class="flex space-between">
        <p class="credit-logos">
          <img src="~assets/images/cards.svg" alt="" />
        </p>
        <p>
          * Denote required fields
        </p>
      </div>
      <div class="checkbox">
        <label>
          <input v-model="data.activate" type="checkbox" value="1" />
          By clicking this box I authorize the Program Administrator to hereby
          activate my Wellness Benefit Program. I understand that my Wellness
          Benefit monthly membership fee will be debited automatically each
          month from my credit card for as long as I remain a member. I
          understand that I will be automatically enrolled in the Family
          Program. I understand I am providing the information on this form
          directly to the Program Administrator to activate my membership. I
          also authorize Wellness Benefits to arrange monthly debits of the
          $19.95 membership fee from my credit card for remittance to the
          Program Administrator until I cancel by calling the toll-free customer
          service at 1-800-878-3733. The Wellness Benefit Program is not
          insurance.
        </label>
      </div>
      <div class="checkbox">
        <label>
          <input type="checkbox" v-model="data.membership" value="" />
          By clicking on the button, I agree to start my membership and pay the
          membership fee each month that I remain a member, and that clicking is
          my electronic signature accepting the programs
          <a href="#" @click.prevent="termsVisible = true">
            Terms and Conditions
          </a>
          , achknowledging receipt of the
          <a href="#" @click.prevent="privacyPolicyVisible = true">
            Program Privacy Policy
          </a>
          and agreeing to the same.
        </label>
      </div>
      <div>
        <input type="submit" value="Submit" />
      </div>
    </form>
    <Modal :visible="termsVisible" @close="termsVisible = false">
      <h5>Terms, Conditions and Disclosures</h5>
      <p>
        This plan is not insurance. This is your agreement as Cardholder with
        Coverdell &amp; Company, Inc. (a "discount plan organization," "DPO").
        It is effective on the date of acceptance of Cardholder’s application
        for enrollment in the Wellness Benefits Program (“Program”) and for the
        period of your plan.
      </p>
      <p>
        DPO shall provide Cardholder with a listing of participating providers.
        Cardholder shall excuse DPO from any liability for errors in such
        listings. Providers are subject to change without notice. Cardholder is
        responsible for choice of provider, verification that the provider is a
        current participant and for payment for goods and services. No portion
        of any provider’s fee will be reimbursed or otherwise paid by DPO.
        Cardholder is solely responsible for payment. Savings are based on the
        provider’s usual fees or on national or regional fees for the service or
        product. Actual savings will vary depending upon your location and the
        specific products or services purchased. Providers may offer certain
        products or services to the general public at prices lower than the
        Program price. In that event, members will always be charged the lower
        price. <span>This is a discount program and not insurance.</span>
        Program discounts cannot be used in conjunction with any other network
        based program.
      </p>
      <p>
        Participating providers are solely responsible for the quality of
        service or product purchased by Cardholder and DPO disclaims any
        liability with respect to such matters. DPO reserves the right to modify
        any benefits, including provider networks, included in Your Program. If
        your state requires that we notify you of changes to your benefits, DPO
        will do so.
      </p>
      <p>
        Payment of membership fee is made by the billing source authorized by
        you in accordance with the payment terms to which you agreed. DPO
        reserves the right to increase or decrease the membership fee for each
        renewal membership term effective upon renewal of your membership. To
        change your method of payment, call the customer service number shown on
        the membership I.D. card. Membership is not transferable. For individual
        memberships, only you may use the membership. If you have an individual
        plus one membership, only you plus one other individual may use the
        membership. For family memberships, only you and anyone living in your
        household may use the membership. Should a single member wish to add
        family plan, call the
      </p>
    </Modal>
    <Modal
      :visible="privacyPolicyVisible"
      @close="privacyPolicyVisible = false"
    >
      <h5>Program Privacy Policy</h5>
      <p>Effective June 2016</p>
      <p>
        This Privacy Policy (“Privacy Policy”) of Coverdell &amp; Company, Inc.
        (“We” “Us” “Our”) explains how We use Personal Identifiable Information
        (“Personal Information”) Users submit and how it is thereafter stored in
        the company’s database. In Our efforts to bring the customer (“Member”
        “You”) of the membership or other program (“The Program”) the Program in
        which You enrolled or requested information, We reserve the right to
        make limited use of basic personal information which You have agreed to
        provide to Us in connection with signing up and/or enrolling in the
        Program. You consent to receive periodic communications from Us and/or
        Our business affiliates regarding Your membership or inquiry, the
        Program and its benefits as well as consent to be contacted by Us or any
        third parties regarding other products or services that may be of
        interest.
      </p>
      <p>
        <strong>What information is collected?</strong> Generally, We gather
        Personal Information that You expressly provide when You sign up to
        receive information and/or enroll in the Program and collect information
        about your transactions with us or our affiliates. This information
        includes, for example, Your name, mailing address, e-mail address, and
        phone number or some other unique personal identifier that We can use to
        confirm sales and billing information (e.g. city of birth or mother's
        maiden name). Occasionally, We may request other information from You
        that may be used by Our Membership Services department to confirm
        enrollment, update Your account or confirm Your order and so that We can
        improve Our program and offerings. If You use one of Our websites, We
        may collect data regarding Your traffic and use of the site. When You
        visit Our websites, cookies are placed on Your hard disk which allows a
        computer to remember who You are and make Your return visits to the
        website more convenient. We recommend that You leave cookies turned onto
        take full advantage of some of Our site features though they are not
        required.
      </p>
      <p>
        <strong>Who is collecting the information?</strong> The Program is
        owned, marketed and/or distributed by Coverdell &amp; Company, Inc. The
        information collected is owned by Us and/or Our marketing partners
        depending on who offered You the Program. Note that this Privacy Policy
        outlines only Coverdell’s policy.
      </p>
    </Modal>
  </div>
</template>
<script>
import SimpleVueValidation from 'simple-vue-validator'
import Modal from '~/components/Modal.vue'
import axios from '~/plugins/axios'
const Validator = SimpleVueValidation.Validator
export default {
  data() {
    return {
      data: {
        Person: {
          FirstName: 'Josh',
          LastName: 'Horner',
          Gender: 'Male',
          PhoneNumber: '1241241245',
          Email: 'josh@bkmediagroup.com',
          DateOfBirth: '03-04-1985'
        },
        Address: {
          Address1: '123 Happy Lane',
          Address2: '',
          City: 'Lafayette',
          State: 'CO',
          PostalCode: '80027',
          CountryCode: 'US'
        },
        Billing: {
          AccountNumber: '4111111111111111'
        },
        exp_date: '12/21'
      },
      privacyPolicyVisible: false,
      termsVisible: false,
      ccOptions: {
        creditCard: true,
        onCreditCardTypeChanged: this.ccChanged
      },
      ccType: 'unknown'
    }
  },
  components: {
    Modal
  },
  methods: {
    submit() {
      this.$validate().then((success) => {
        if (success) {
          axios.post('', this.data).then(
            (response) => {
              console.log(response)
            },
            (error) => {
              console.log(error)
            }
          )
        }
      })
    },
    ccChanged(type) {
      this.ccType = type
    }
  },
  validators: {
    'data.Person.Email': (value = '') => {
      return Validator.value(value)
        .required()
        .email()
    },
    'data.Person.FirstName': (value = '') => {
      return Validator.value(value).required()
    },
    'data.Person.LastName': (value = '') => {
      return Validator.value(value).required()
    },
    'data.Person.Gender': (value = '') => {
      return Validator.value(value).required()
    },
    'data.Person.DateOfBirth': (value = '') => {
      return Validator.value(value).required()
    },
    'data.Person.Address1': (value = '') => {
      return Validator.value(value).required()
    }
  }
}
</script>
