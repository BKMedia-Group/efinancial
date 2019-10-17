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
            <Form />
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
  </div>
</template>
<script>
import Form from '~/components/Form.vue'
export default {
  data() {
    return {
      isVisible1: false,
      isVisible2: false,
      data: {}
    }
  },
  methods: {
    submit() {}
  },
  components: {
    Form
  }
}
</script>
