<template>
  <div>
    <div class="hero">
      <div class="container">
        <div class="row">
          <div class="col-6">
            <h1>Welcome to the Future of Your Good Health</h1>
            <p>
              As a valued eFinancial customer, and Fidelity Life policyholder,
              we have arranged for you to participate in a new Wellness Benefit
              Program to help you reduce the amount of money you pay
              out-of-pocket for health care and wellness services, for you and
              every member of your household.
            </p>
          </div>
        </div>
      </div>
    </div>
    <div class="section_1">
      <div class="container">
        <div class="row justify-content-center">
          <div class="col-9 text-center">
            <h2>Your Wellness Benefit Program</h2>
            <p>
              This program includes savings on medical products and services for
              you and your entire family that many health insurance plans may
              not cover. eFinancial’s Wellness Benefit Services include:
            </p>
          </div>
        </div>
        <div class="row">
          <div class="col-6">
            <h4>Telemedicine</h4>
            <p>
              For any household member needing medical attention, you can call 7
              days a week 24 hours a day. 94% of all medical problems are
              resolved with these calls by the medical provider ordering a
              prescription or advising you of treatment over the phone. You will
              receive your access information when we send you your benefits
              card.
            </p>
            <h4>Prescriptions</h4>
            <p>
              Members can save from 10% to 85% on name brand and generic
              prescriptions at over 65,000 select pharmacies nationwide or when
              using the mail order service.
            </p>
            <h4>Dental</h4>
            <p>
              Members can save 15% to 50% per visit, in most instances, on
              services at any of the many available dental practice locations
              nationwide.
            </p>
          </div>
          <div class="col-6">
            <h4>Vision</h4>
            <p>
              Members can save 10% to 60% off eyeglasses, contact lenses and
              other retail eyewear items, as well as 10% to 30% off eye
              examinations and 40% to 50% off the national average on LASIK.
            </p>
            <h4>Hearing</h4>
            <p>
              Members can save 17% to 40% off retail pricing of digital hearing
              aids.
            </p>
            <h4>Chiropractic</h4>
            <p>
              Members can save 20% to 40% on Chiropractic fees at participating
              chiropractors across the country.
            </p>
            <h4>Alternative Medicine</h4>
            <p>
              This program helps member save 20% on services, including:
              Acupuncture, Massage Therapy, Nutritional Counseling,
              Meditation/Relaxation, and Naturopathy.
            </p>
          </div>
        </div>
      </div>
    </div>
    <div class="form_section">
      <div class="container">
        <h2 class="text-center">Get your Wellness Benefit today!</h2>
        <div class="row justify-content-center">
          <div class="col-6">
            <form
              id="app"
              @submit="checkForm()"
              action="https://vuejs.org/"
              method="post"
              novalidate="true"
            >
              <p>
                <input
                  id="firstName"
                  v-model="firstName"
                  type="text"
                  name="firstName"
                  placeholder="First Name*"
                  required
                />
                <input
                  id="lastName"
                  v-model="lastName"
                  type="text"
                  name="lastName"
                  placeholder="Last Name*"
                  required
                />
              </p>
              <p>
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
              </p>
              <p>
                <input
                  id="email"
                  v-model="email"
                  type="email"
                  name="email"
                  placeholder="Email Address*"
                />
                <input
                  id="phone"
                  v-model="phone"
                  type="tel"
                  name="phone"
                  placeholder="Phone Number"
                />
              </p>
              <p>
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
                <input
                  id="cvv"
                  v-model="cvv"
                  type="text"
                  name="cvv"
                  placeholder="CVV"
                />
              </p>
              <p class="form_image_required">
                <img src="~assets/images/cards.svg" alt="" />
                <span>
                  * Denote required fields
                </span>
              </p>
              <p>
                <label>
                  <input
                    id="checkbox1"
                    type="checkbox"
                    name="activate"
                    value=""
                    v-model="activate"
                  />
                  By clicking this box I authorize the Program Administrator to
                  hereby activate my Wellness Benefit Program. I understand that
                  my Wellness Benefit monthly membership fee will be debited
                  automatically each month from my credit card for as long as I
                  remain a member. I understand that I will be automatically
                  enrolled in the Family Program. I understand I am providing
                  the information on this form directly to the Program
                  Administrator to activate my membership. I also authorize
                  Wellness Benefits to arrange monthly debits of the $19.95
                  membership fee from my credit card for remittance to the
                  Program Administrator until I cancel by calling the toll-free
                  customer service at 1-800-878-3733. The Wellness Benefit
                  Program is not insurance.
                </label>
                <label>
                  <input
                    id="checkbox2"
                    type="checkbox"
                    name="membership"
                    value=""
                    v-model="membership"
                  />
                  By clicking on the button, I agree to start my membership and
                  pay the membership fee each month that I remain a member, and
                  that clicking is my electronic signature accepting the
                  programs
                  <a href="javascript:void()" @click="isVisible1 = true">
                    Terms and Conditions
                  </a>
                  , achknowledging receipt of the
                  <a href="javascript:void()" @click="isVisible2 = true">
                    Program Privacy Policy
                  </a>
                  and agreeing to the same.
                </label>
              </p>
              <p>
                <input type="submit" value="Submit" />
              </p>
            </form>
          </div>
        </div>
      </div>
    </div>
    <Modal :visible="isVisible1" @close="isVisible1 = false">
      content 1
    </Modal>
    <Modal :visible="isVisible2" @close="isVisible2 = false">
      content 2
    </Modal>
    <button type="button" name="button" @click="isVisible1 = true">
      Show
    </button>
    <button type="button" name="button" @click="isVisible2 = true">
      Show 2
    </button>
  </div>
</template>
<script>
import Modal from '~/components/Modal.vue'
export default {
  data() {
    return {
      isVisible1: false,
      isVisible2: false,
      gender: '',
      lastName: '',
      firstName: '',
      email: '',
      membership: '',
      activate: '',
      cc_number: '',
      cvv: '',
      exp_date: '',
      dob: '',
      phone: ''
    }
  },
  methods: {
    checkform() {}
  },
  components: {
    Modal
  }
}
</script>
