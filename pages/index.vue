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
    <section class="section_1">
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
    </section>
    <section class="form_section">
      <div class="container">
        <h2 class="text-center">Get your Wellness Benefit today!</h2>
        <div class="row justify-content-center">
          <div class="col-7 text-center">
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
              <p class="cc_wrap">
                <input
                  id="cc_number"
                  v-model="cc_number"
                  type="text"
                  name="cc_number"
                  placeholder="Credit Card Number*"
                />
                <input
                  id="exp_date"
                  v-model="exp_date"
                  type="text"
                  name="exp_date"
                  placeholder="MM/YY*"
                />
                <input
                  id="cvv"
                  v-model="cvv"
                  type="text"
                  name="cvv"
                  placeholder="CVV*"
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
                  <a href="javascript:void(0)" @click="isVisible1 = true">
                    Terms and Conditions
                  </a>
                  , achknowledging receipt of the
                  <a href="javascript:void(0)" @click="isVisible2 = true">
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
    </section>
    <section class="section_4">
      <div class="container">
        <div class="row justify-content-center">
          <div class="col-7 text-center">
            <h2>Your satisfaction is guaranteed.</h2>
            <p>
              If you are not happy with your Wellness Benefits, please call
              <a href="tel:1-800-878-3733">1-800-878-3733</a> within 30 days of
              the effective date for a full refund of the fees paid.
            </p>
          </div>
        </div>
      </div>
    </section>
    <Modal :visible="isVisible1" @close="isVisible1 = false">
      <h5>Terms, Conditions and Disclosures</h5>
      <p>
        This plan is not insurance. This is your agreement as Cardholder with
        Coverdell & Company, Inc. (a "discount plan organization," "DPO"). It is
        effective on the date of acceptance of Cardholder’s application for
        enrollment in the Wellness Benefits Program (“Program”) and for the
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
        price. <strong>This is a discount program and not insurance.</strong>
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
    <Modal :visible="isVisible2" @close="isVisible2 = false">
      <h5>Program Privacy Policy</h5>
      <p>Effective June 2016</p>
      <p>
        This Privacy Policy (“Privacy Policy”) of Coverdell & Company, Inc.
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
        owned, marketed and/or distributed by Coverdell & Company, Inc. The
        information collected is owned by Us and/or Our marketing partners
        depending on who offered You the Program. Note that this Privacy Policy
        outlines only Coverdell’s policy.
      </p>
    </Modal>
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
