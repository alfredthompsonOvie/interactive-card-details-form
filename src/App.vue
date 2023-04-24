<template>
  <section class="container">
    <section class="cards">
      <section class="cards__contents">
        <section class="card card__front">
          <img class="logo" src="@/assets/images/card-logo.svg" alt="atm card logo">
          <!-- <img src="@/assets/images/icon-complete.svg" alt="atm card logo"> -->
          <section class="card__details">
            <section class="card__number">
              <p>0000 0000 0000 0000</p>
            </section>
            <section class="card__profile">
              <p class="card__profile__name">
                jane appleseed
              </p>
              <p class="card__profile__exp">
                <span>00</span>/<span>00</span>  
              </p>
            </section>
          </section>
        </section>
        <section class="card card__back">
          <section class="cvc">000</section>
        </section>
      </section>
    </section>
    <section class="form__container">
      <form>
        <section class="form__control">
          <label for="fullname">Cardholder Name</label>
          <input 
          type="text"
          placeholder="e.g. Jane Appleseed"
          name="fullname"
          id="fullname"
          class="form__field"
          >
        </section>

        <section class="form__control">
          <label for="cardNumber">Card Number</label>
          <input 
          type="text"
          placeholder="e.g. 1234 5678 9123 0000"
          name="cardNumber"
          id="cardNumber"
          class="form__field"
          >
        </section>
        <section class="form__group">
          <fieldset>
            <legend>Exp. Date (MM/YY)</legend>
            <section class="form__control">
              <label for="exp--month"></label>
              <input 
              type="text"
              placeholder="MM"
              name="exp--month"
              id="exp--month"
              class="form__field exp"
              >
            </section>
  
            <section class="form__control">
              <label for="exp--year"></label>
              <input 
              type="text"
              placeholder="YY"
              name="exp--year"
              id="exp--year"
              class="form__field exp"
              >
            </section>
          </fieldset>

          <section class="form__control">
            <label for="cvc">CVC</label>
            <input 
            type="text"
            placeholder="e.g. 123"
            name="cvcr"
            id="cvc"
            class="form__field form__field--cvc"
            >
          </section>
        </section>

        <button type="submit">Confirm</button>
      </form>
    </section>
  </section>
</template>

<script setup>

</script>

<style scoped>
form  {
  padding: 0 1em;
  margin-top: 6em;
  /* background-color: red; */
  margin-inline: auto;
  max-width: 400px;
  width: 100%;
}

.form__control + .form__control {
  margin-top: 1em;
}
label {
  text-transform: uppercase;
}
.form__field {
  padding: 1em;
  display: block;
  width: 100%;
  /* border: 1px solid var(--LinearGradient-active_input_border); */
  border-radius: 4px;
  /* border-image: linear-gradient(to bottom, var(--LinearGradient-active_input_border)); */
}
.form__group {
  margin-top: 1em;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  /* flex-wrap: wrap; */
  gap: .7em;
}
fieldset {
  display: flex;
  gap: .5em;
  border: 0;
  /* margin-right: auto; */
}
.form__group .form__control {
  margin-top: 0;
}
.form__field.exp {
  max-width: 4em;
}
.form__field.form__field--cvc {
  /* margin-left: auto; */
}
button[type='submit']{
  background-color: var(--VeryDarkViolet);
  width: 100%;
  padding: 1em;
  color: var(--White);
  border: 0;
  margin-top: 1em;
  border-radius: 4px;

}
/* ::placeholder {

} */
</style>


git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/alfredthompsonOvie/interactive-card-details-form.git
git push -u origin main