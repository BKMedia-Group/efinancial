<template>
  <div>
    <form novalidate @submit.prevent="submit()" id="form">
      <div v-if="globalError != ''" class="global-error">
        {{ globalError }}
      </div>
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
      <div
        class="input"
        :class="{
          error: validation.hasError('data.Person.Address.Address1')
        }"
      >
        <input
          v-model="data.Person.Address.Address1"
          type="text"
          placeholder="Address*"
        />
        <div class="message">
          {{ validation.firstError('data.Person.Address.Address1') }}
        </div>
      </div>
      <div class="form-row city-state-zip">
        <div class="col" id="city">
          <div
            class="input"
            :class="{ error: validation.hasError('data.Person.Address.City') }"
          >
            <input
              v-model="data.Person.Address.City"
              type="text"
              placeholder="City*"
            />
            <div class="message">
              {{ validation.firstError('data.Person.Address.City') }}
            </div>
          </div>
        </div>
        <div class="col" id="state">
          <div
            class="input"
            :class="{ error: validation.hasError('data.Person.Address.State') }"
          >
            <select
              v-model="data.Person.Address.State"
              ref="data.Person.Address.State"
            >
              <option value="">State*</option>
              <option
                v-for="(state, abbr) in usStates"
                :value="abbr"
                :key="abbr"
              >
                {{ state }}
              </option>
            </select>
            <div class="message">
              {{ validation.firstError('data.Person.Address.State') }}
            </div>
          </div>
        </div>
        <div class="col" id="zip">
          <div
            class="input"
            :class="{
              error: validation.hasError('data.Person.Address.PostalCode')
            }"
          >
            <input
              v-model="data.Person.Address.PostalCode"
              type="text"
              placeholder="PostalCode*"
            />
            <div class="message">
              {{ validation.firstError('data.Person.Address.PostalCode') }}
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
              <option diabled value="">Select Gender*</option>
              <option value="77">Male</option>
              <option value="70">Female</option>
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
                datePattern: ['m', 'd', 'Y'],
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
      <div
        class="input cc"
        :class="{
          error:
            validation.hasError('data.Billing.AccountNumber') ||
            validation.hasError('data.exp_date')
        }"
      >
        <div class="input" id="cc_number">
          <cleave
            v-model="data.Billing.AccountNumber"
            ref="data.Billing.AccountNumber"
            :options="ccOptions"
            placeholder="Credit Card Number"
          ></cleave>
          <div class="message">
            {{ validation.firstError('data.Billing.AccountNumber') }}
          </div>
        </div>
        <div class="input" id="exp_date">
          <cleave
            v-model="data.exp_date"
            ref="data.exp_date"
            :options="{ date: true, datePattern: ['m', 'y'] }"
            placeholder="MM/YY"
          ></cleave>
          <div class="message">
            {{ validation.firstError('data.exp_date') }}
          </div>
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
      <div
        class="checkbox"
        :class="{
          error: validation.hasError('activate')
        }"
      >
        <label>
          <input v-model="activate" type="checkbox" />
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
        <div class="message">
          {{ validation.firstError('activate') }}
        </div>
      </div>
      <div
        class="checkbox"
        :class="{
          error: validation.hasError('membership')
        }"
      >
        <label>
          <input v-model="membership" type="checkbox" />
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
        <div class="message">
          {{ validation.firstError('membership') }}
        </div>
      </div>
      <div>
        <input type="submit" value="Submit" :disabled="submitting" />
      </div>
    </form>
    <Modal :visible="successVisible" @close="successVisible = false">
      <h5>Congratulations on your enrollment.</h5>
      <p>
        Thank you for signing up! Please be on the lookout for your offline
        materials.
      </p>
    </Modal>
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
        family plan, call the customer service number shown on the membership
        I.D. Card.
      </p>
      <p>
        <span>General Complaint Procedure.</span> Complaints of any nature may
        be filed with Coverdell & Company, Inc. the discount plan organization
        at 8770 W. Bryn Mawr, Suite 1000, Chicago, IL 60631. Complaints will be
        acknowledged in writing within 5 business days and will be resolved in
        writing to you within 30 calendar days. Should you remain dissatisfied
        with the results from your complaint with the discount plan
        organization, you may contact the Commissioner of Insurance, Division of
        Insurance, the insurance department, or other agency which regulates
        this product in your state. Contact us at 1-800-308-0374 to obtain state
        complaint contact information.
      </p>
      <p>
        <span>Termination and Cancellation.</span> You may terminate this at any
        time by logging in to www.findbestbenefits.com and submitting a
        cancellation request on the Contact Us page, calling us at the toll free
        number on your membership card, or you may notify us in writing at
        Member Services, 8770 W. Bryn Mawr, Suite 1000, Chicago, IL 60631. Your
        cancellation will be effective promptly upon the receipt of your
        cancellation notice and you will no longer be billed for your
        membership. DPO reserves the right to terminate your membership at any
        time for any reason.
      </p>
      <p>
        <span>
          All Members: You have the right to cancel this plan within 30 days
          after the effective date for a full refund of fees paid.
        </span>
      </p>
      <p>
        Annual Members Only: After the first 30 days, if a membership is
        cancelled by You or DPO for any reason other than nonpayment of fees,
        You are eligible for a pro-rata refund of membership fees.
      </p>
      <p>
        <span>Governing Law and Arbitration.</span> This agreement and its
        interpretation and enforcement shall be governed and controlled by the
        laws of the State of Illinois. Any dispute arising from or related to
        this agreement shall be resolved by binding, non-appealable private
        arbitration conducted in accordance with the Rules of American
        Arbitration Association in Chicago, Illinois, unless required by a
        member’s individual state laws to resolve in a different location. This
        provision shall survive the termination of this agreement and its
        interpretation shall be subject to the Federal Arbitration Act.
      </p>
      <p>
        <span>
          Governing Law and Arbitration for Montana and Oklahoma Residents.
        </span>
        Your membership is governed and controlled by the laws of your state.
        Any dispute arising from or related to Your membership shall be resolved
        by a voluntary private arbitration conducted in accordance with the
        Rules of the American Arbitration Association in your state. This
        provision shall survive the termination of Your membership and shall be
        subject to the Federal Arbitration Act.
      </p>
      <p>
        <span>South Dakota Residents.</span> If you cancel the program you are
        not obligated to make further payments for the program, nor are you
        entitled to any program benefits for any period of time after the last
        month for which payment has been made.
      </p>
      <p>
        <span class="large">Disclosure. This plan is NOT insurance.</span> This
        plan is not a qualified health plan under the Affordable Care Act (ACA).
        Some services may be covered by a qualified health plan under the ACA.
        This plan does not meet the minimum creditable coverage requirements
        under M.G.L. c. 111M and 956 CMR 5.00. This is not a Medicare
        prescription drug plan. Discounts on hospital services are not available
        in Maryland. The plan provides discounts at certain health care
        providers of medical services. The plan does not make payments directly
        to the providers of medical services. The plan member is obligated to
        pay for all health care services but will receive a discount from those
        health care providers who have contracted with the discount plan
        organization. The range of discounts will vary depending on the provider
        type and services provided. The licensed discount plan organization is
        Coverdell & Company, Inc., at 8770 W. Bryn Mawr, Suite 1000, Chicago, IL
        60631, 1-800-308-0374. To view a list of participating providers visit
        www.findbestbenefits.com.
        <span>
          You have the right to cancel this plan within 30 days of the effective
          date for a full refund of fees paid. Such refunds are issued within 30
          days of cancellation.
        </span>
      </p>
      <p><span class="large center">This is not insurance</span></p>
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
      <p>
        <strong>How do We use the information collected?</strong> We use the
        Personal Information You provide to Us to service Your Program
        membership and store in Our database to contact You about future
        Programs or other offers. For example, We request Your mailing address
        so We know where to send the Program Material and any other information
        You may request. We also may send You additional membership information
        such as updates about Our Program or other programs that may be of
        interest to You. We use Your credit card information to bill You for the
        membership fee. We may use Your email address to notify You of Program
        updates and to further provide You with additional product information
        and opportunities of membership or offers. The Personal Information that
        is collected may also be shared with other groups within the Coverdell
        organization, and with Coverdell’s affiliates and/or marketing partners
        depending on who offered You membership in the program. If Your Program
        involves the use of one of Our websites, the technical and statistical
        information that is automatically collected from Your computer whenever
        You visit Our website is used to help Us improve the site and the member
        experience. From time to time We may disclose general statistical
        information about Our website and its visitors such as the number of
        visitors, the number and type of products purchased, etc.
      </p>
      <p>
        <strong>Do you share personal information with third parties?</strong>
        We may share Personal Information You provide us and information about
        your transactions with third parties whom We employ to perform functions
        on Our behalf, and as permitted by law. For example, We use a third
        party to verify and process Your credit card information in order to
        charge You for Your Membership fee. All third parties are contractually
        obligated to use Personal Information only for the purpose for which it
        is given. We are not responsible for the information practices of third
        parties. The collection, use and disclosure of information by third
        parties are subject to their respective privacy policies, which may
        differ from Our policy.
      </p>
      <p>
        From time to time, We may also share Personal Information You Provide us
        and information about your transactions with Our affiliates and/or
        marketing partners or unaffiliated third parties who offer products and
        services We think will be of interest to You.
      </p>
      <p>
        Furthermore, limited customer information may potentially be transferred
        as a business asset of Coverdell & Company, Inc. As We continue to
        develop Our business, We may buy or sell assets. In such transactions,
        customer information generally is one of the transferred business
        assets. Also, in the event that Our company or substantially all of its
        assets are acquired, customer information will of course be one of the
        transferred assets. In the event that customer information is
        transferred as described in this paragraph, members may be notified and
        have the ability to opt-out of having their personal information
        transferred to any new entity.
      </p>
      <p>
        <strong>How do I change/modify my information?</strong> You can change,
        modify or update Your member information simply by calling the customer
        service number on Your membership card.
      </p>
      <p>
        <strong>How do you secure member information?</strong> Data Security is
        a critical issue for Coverdell. Credit card data is always protected
        during transmission between Our websites and administrative environment
        through the use of SSL technology. Once received at Our administrative
        center, data is encrypted, and access to data is protected through
        multiple controls and security practices in accordance with PCI
        standards. Coverdell is a PCI certified organization.
      </p>
      <p>
        Internal access to member information is protected and can only be
        accessed by password. We also contract with industry experts to
        institute and review web and other security on a periodic basis.
      </p>
      <p>
        <strong>How do you update your Privacy Policy?</strong> We will notify
        You in advance if there is a material change in Our privacy practices.
        Additionally, We will post any changes to this Privacy Policy to Our
        websites if Your Program involves the use of a website.
      </p>
      <p>
        <strong>How do I contact the Program or opt out?</strong> If You have
        any questions about the practices of this Program, Your dealings with
        any of Our websites, or to opt out of information sharing and be placed
        on Our Do Not Contact List, You can contact Us at 1-800-308-0374.
      </p>
      <p>
        By using any of Our websites, if applicable, You consent to the
        collection and use of information as it is disclosed in this Privacy
        Policy statement. You are obligated to immediately inform us if and when
        any telephone number You provided to Us changes or is no longer in use.
        If You do not agree We ask that You contact Us to opt out of information
        sharing and do not use Our site. Thank You.
      </p>
      <p>Effective June 2016</p>
    </Modal>
  </div>
</template>
<script>
import SimpleVueValidation from 'simple-vue-validator'
import Modal from '~/components/Modal.vue'
import axios from '~/plugins/axios'
import usStates from '~/plugins/states'
const VueScrollTo = require('vue-scrollto')
const Validator = SimpleVueValidation.Validator
export default {
  data() {
    return {
      data: {
        Person: {
          Address: {
            State: ''
          },
          Gender: '',
          DateOfBirth: ''
        },
        Billing: {},
        exp_date: ''
      },
      privacyPolicyVisible: false,
      termsVisible: false,
      successVisible: false,
      ccOptions: {
        creditCard: true,
        onCreditCardTypeChanged: this.ccChanged
      },
      ccType: 'unknown',
      usStates,
      globalError: '',
      activate: false,
      membership: false,
      submitting: false
    }
  },
  components: {
    Modal
  },
  methods: {
    methodOfPayment() {
      switch (this.ccType) {
        case 'visa':
          return 5
        case 'amex':
          return 1
        case 'mastercard':
          return 4
        case 'discover':
          return 2
      }
    },
    submit() {
      this.globalError = ''
      this.$validate().then((success) => {
        if (success) {
          this.submitting = true
          const postData = this.data
          postData.Billing.MethodOfPayment = this.methodOfPayment()
          axios
            .post('', this.data)
            .then((response) => {
              this.reset()
              this.successVisible = true
            })
            .catch((error) => {
              VueScrollTo.scrollTo('#form', 500)
              this.globalError = error.response.data.ErrorMessage
            })
            .finally(() => {
              this.submitting = false
            })
        } else {
          this.globalError = 'Please correct the highlighted fields below'
          VueScrollTo.scrollTo('#form', 500)
        }
      })
    },
    reset() {
      this.data = {
        Person: {
          Address: {
            State: ''
          },
          Gender: '',
          DateOfBirth: ''
        },
        Billing: {},
        exp_date: ''
      }
      this.activate = false
      this.membership = false
      this.validation.reset()
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
    'data.Person.Address.Address1': (value = '') => {
      return Validator.value(value).required()
    },
    'data.Person.Address.City': (value = '') => {
      return Validator.value(value).required()
    },
    'data.Person.Address.State': (value = '') => {
      return Validator.value(value).required()
    },
    'data.Person.Address.PostalCode': (value = '') => {
      return Validator.value(value).required()
    },
    'data.Billing.AccountNumber': (value = '') => {
      return Validator.value(value).required()
    },
    'data.exp_date': (value = '') => {
      return Validator.value(value).required()
    },
    activate: (value = '') => {
      if (!value) {
        value = ''
      }
      return Validator.value(value).required()
    },
    membership: (value = '') => {
      if (!value) {
        value = ''
      }
      return Validator.value(value).required()
    }
  }
}
</script>
