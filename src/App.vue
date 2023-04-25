<template>
	<section class="container">
		<section class="cards">
			<section class="cards__contents">
				<section class="card card__front">
					<img
						class="logo"
						src="@/assets/images/card-logo.svg"
						alt="atm card logo"
					/>
					<!-- <img src="@/assets/images/icon-complete.svg" alt="atm card logo"> -->
					<section class="card__details">
						<section class="card__number">
							<p>0000 0000 0000 0000</p>
						</section>
						<section class="card__profile">
							<p class="card__profile__name">jane appleseed</p>
							<p class="card__profile__exp"><span>00</span>/<span>00</span></p>
						</section>
					</section>
				</section>
				<section class="card card__back">
					<section class="cvc">000</section>
				</section>
			</section>
		</section>
		<section class="form__container">
			<form @submit="onSubmit">
				<section class="form__control">
					<label for="fullname">Cardholder Name</label>
					<input
						type="text"
						placeholder="e.g. Jane Appleseed"
						name="fullname"
						id="fullname"
            v-model="fullname"
						class="form__field"
            :class="{ 'form__field--error': errors.fullname }"
					/>
					<span class="form__field--border"></span>
          <span class="error"> {{ errors.fullname }}</span>

				</section>

				<section class="form__control">
					<label for="cardNumber">Card Number</label>
					<input
						type="text"
						placeholder="e.g. 1234 5678 9123 0000"
						name="cardNumber"
						id="cardNumber"
            v-model="cardNumber"
						class="form__field"
            :class="{ 'form__field--error': errors.cardNumber }"
					/>
					<span class="form__field--border"></span>
          <span class="error"> {{ errors.cardNumber }}</span>

				</section>
				<section class="form__group">
					<fieldset>
						<legend>Exp. Date (MM/YY)</legend>
						<section class="form__control">
							<label for="expMonth"></label>
							<input
								type="text"
								placeholder="MM"
								name="expMonth"
								id="expMonth"
                v-model="expMonth"
								class="form__field exp"
                :class="{ 'form__field--error': errors.expMonth }"
							/>
							<span class="form__field--border"></span>
          <span class="error"> {{ errors.expMonth }}</span>

						</section>

						<section class="form__control">
							<label for="expYear"></label>
							<input
								type="text"
								placeholder="YY"
								name="expYear"
								id="expYear"
                v-model="expYear"
								class="form__field exp"
                :class="{ 'form__field--error': errors.expYear }"
                />
							<span class="form__field--border"></span>
          <span class="error"> {{ errors.expYear }}</span>


						</section>
					</fieldset>

					<section class="form__control">
						<label for="cvc">CVC</label>
						<input
							type="text"
							placeholder="e.g. 123"
							name="cvc"
							id="cvc"
              v-model="cvc"
							class="form__field form__field--cvc"
              :class="{ 'form__field--error': errors.cvc }"
						/>
						<span class="form__field--border"></span>
          <span class="error"> {{ errors.cvc }}</span>

					</section>
				</section>

				<button type="submit">Confirm</button>
			</form>
		</section>
	</section>
</template>

<script setup>
import { useField, useForm } from 'vee-validate';
import { object, string, number } from 'yup';

const schema = object({
  fullname: string().required("Your fullname is required"),
  cardNumber: number().required("Wrong format, numbers only"),
  expMonth: number().required("Can't be blank"),
  expYear: number().required("Can't be blank"),
  cvc: number().required("Can't be blank").min(3 | "minimum of 3").max(3 | "must be 3"),
});

const { handleSubmit, errors } = useForm({
  validationSchema: schema
});
const { value: fullname } = useField('fullname');
const { value: cardNumber } = useField('cardNumber');
const { value: expMonth } = useField('expMonth');
const { value: expYear } = useField('expYear');
const { value: cvc } = useField('cvc');

const onSubmit = handleSubmit((values) => {
  console.log(values);
});
</script>

<style scoped>
form {
	padding: 0 1em;
	margin-top: 6em;
	/* background-color: red; */
	margin-inline: auto;
	max-width: 400px;
	width: 100%;
}

.form__control + .form__control {
	margin-top: 1.4em;
}
.form__control {
	position: relative;
	/* padding: 0px 3px 2.5px; */
	padding: 0px 2px 1.5px;
}
label {
	text-transform: uppercase;
	margin-bottom: 0.4em;
	display: block;
  /* font-size: .8rem; */
}
.form__field {
	padding: 1em;
	display: block;
	width: 100%;
  height: 3em;
	border: 1px solid var(--LightGrayishViolet);
	border-radius: 4px;
	position: relative;
	margin: 0.1px;
	z-index: 2;
}
.form__field:focus {
	border: 0;
	outline: 0;
}
.form__field--border {
	position: absolute;
	bottom: 0;
	left: 0;
	/* 
   */
	/* border: 1px solid red; */
	/* background-color: red; */
	width: 100%;
	/* height: 3em;
	height: 2.85em; */
	height: 2.75em;
	padding: 2px;
	display: block;
	border-radius: 6px;
	background-repeat: no-repeat;
	background-position: center;
	background-size: cover;
	/* background-image: var(--LinearGradient-active_input_border); */

	z-index: 1;
}
.form__field:focus + .form__field--border {
	background-image: var(--LinearGradient-active_input_border);
}
.form__field--error {
  border: 1px solid var(--Red_input_errors);
}
.error {
  color: var(--Red_input_errors);
  font-size: .8rem;
  position: absolute;
}
.form__group {
	margin-top: 1em;
	display: flex;
	align-items: flex-end;
	justify-content: space-between;
	/* flex-wrap: wrap; */
	gap: 0.7em;
}
fieldset {
	display: flex;
  justify-content: center;
	gap: 0.5em;
	border: 0;
  /* margin-right: auto; */
}
legend {
  font-size: .9rem;
}
.form__group .form__control {
	margin-top: 0;
}
.form__field.exp {
	max-width: 5em;
  width: 100%;
}
.form__field--cvc {
	/* margin-left: auto; */
}
button[type="submit"] {
	background-color: var(--VeryDarkViolet);
	width: 100%;
	padding: 1em;
	color: var(--White);
	border: 0;
	margin-top: 1.5em;
	border-radius: 4px;
  /* font-size: 1rem; */
}
@media (min-width: 992px) {
  form {
    margin-top: 0em;
  }
}
</style>
