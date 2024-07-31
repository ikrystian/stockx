<script lang="ts">
    import {z} from 'zod'

    import formImage1 from '../assets/form_1.svg';
    import formImage2 from '../assets/form_2.svg';
    import formImage3 from '../assets/form_3.svg';
    import {ZodFormStore} from "@nerd-coder/svelte-zod-form";

    const formSchema = z.object({
        firstName: z.string(),
        lastName: z.string(),
        street: z.string(),
        postalCode: z.string(),
        city: z.string(),
        phone: z.string(),
        email: z.string().email(),
    });

    const form = new ZodFormStore(formSchema, {
        debug: true,
        onSubmit: async(values) => {
            await new Promise((r) => setTimeout(r, 2000))
            console.log('Submitted values:', values)
        }
    });

    const {
        firstName_value,
        firstName_error,
        firstName_valid,
        firstName_dirty,
        firstName_touched,

        lastName_value,
        lastName_error,
        lastName_valid,
        lastName_dirty,
        lastName_touched,

        street_value,
        street_error,
        street_valid,
        street_dirty,
        street_touched,

        postalCode_value,
        postalCode_error,
        postalCode_valid,
        postalCode_dirty,
        postalCode_touched,

        city_value,
        city_error,
        city_valid,
        city_dirty,
        city_touched,

        phone_value,
        phone_error,
        phone_valid,
        phone_dirty,
        phone_touched,

        email_value,
        email_error,
        email_valid,
        email_dirty,
        email_touched,
    } = form.stores
    const { submitting, valid, model } = form

</script>

<section class="form-section">
    <form class="form" on:submit|preventDefault={form.triggerSubmit}>
        <h2 class="form__title">Enter details</h2>
        <div class="form__row">
            <div class="form__group">
                <label class="form__label" for="firstName">First name</label>
                <input
                        name="firstName"
                        on:input={form.fields.firstName.handleChange}
                        on:blur={form.fields.firstName.handleBlur}
                        type="text"
                        class="form__input"
                        placeholder="First name"
                        value={$firstName_value || ''}
                        class:form__input--invalid={!$firstName_valid && $firstName_touched}
                        class:form__input--valid={$firstName_valid && $firstName_dirty}
                />
                {#if $firstName_error && $firstName_touched}<p>{$firstName_error}</p>{/if}
            </div>

            <div class="form__group">
                <label class="form__label" for="lastName">Last name</label>
                <input
                        name="lastName"
                        on:input={form.fields.lastName.handleChange}
                        on:blur={form.fields.lastName.handleBlur}
                        type="text"
                        class="form__input"
                        placeholder="Last name"
                        value={$lastName_value || ''}
                        class:form__input--invalid={!$lastName_valid && $lastName_touched}
                        class:form__input--valid={$lastName_valid && $lastName_dirty}
                />
                {#if $lastName_error && $lastName_touched}<p>{$lastName_error}</p>{/if}
            </div>

        </div>

        <div class="form__group">
            <label class="form__label" for="street">Street</label>
            <input
                    name="street"
                    on:input={form.fields.street.handleChange}
                    on:blur={form.fields.street.handleBlur}
                    type="text"
                    class="form__input"
                    placeholder="Street"
                    value={$street_value || ''}
                    class:form__input--invalid={!$street_valid && $street_touched}
                    class:form__input--valid={$street_valid && $street_dirty}
            />
            {#if $street_error && $street_touched}<p>{$street_error}</p>{/if}
        </div>

        <div class="form__row">

            <div class="form__group">
                <label class="form__label" for="postalCode">Postal code</label>
                <input
                        name="postalCode"
                        on:input={form.fields.postalCode.handleChange}
                        on:blur={form.fields.postalCode.handleBlur}
                        type="text"
                        class="form__input"
                        placeholder="Postal code"
                        value={$postalCode_value || ''}
                        class:form__input--invalid={!$postalCode_valid && $postalCode_touched}
                        class:form__input--valid={$postalCode_valid && $postalCode_dirty}
                />
                {#if $postalCode_error && $postalCode_touched}<p>{$postalCode_error}</p>{/if}
            </div>

            <div class="form__group">
                <label class="form__label" for="city">City</label>
                <input
                        name="city"
                        on:input={form.fields.city.handleChange}
                        on:blur={form.fields.city.handleBlur}
                        type="text"
                        class="form__input"
                        placeholder="City"
                        value={$city_value || ''}
                        class:form__input--invalid={!$city_valid && $city_touched}
                        class:form__input--valid={$city_valid && $city_dirty}
                />
                {#if $city_error && $city_touched}<p>{$city_error}</p>{/if}
            </div>

        </div>

        <div class="form__group">
            <label class="form__label" for="phone">Phone number</label>
            <input
                    name="phone"
                    on:input={form.fields.phone.handleChange}
                    on:blur={form.fields.phone.handleBlur}
                    type="tel"
                    class="form__input"
                    placeholder="Phone number"
                    value={$phone_value || ''}
                    class:form__input--invalid={!$phone_valid && $phone_touched}
                    class:form__input--valid={$phone_valid && $phone_dirty}
            />
            {#if $phone_error && $phone_touched}<p>{$phone_error}</p>{/if}
        </div>

        <div class="form__group">
            <label class="form__label" for="email">E-mail</label>
            <input
                    name="email"
                    on:input={form.fields.email.handleChange}
                    on:blur={form.fields.email.handleBlur}
                    type="email"
                    class="form__input"
                    placeholder="E-mail"
                    value={$email_value || ''}
                    class:form__input--invalid={!$email_valid && $email_touched}
                    class:form__input--valid={$email_valid && $email_dirty}
            />
            {#if $email_error && $email_touched}<p>{$email_error}</p>{/if}
        </div>

        <button  class="form__button" type="submit" disabled={!$valid || $submitting}>
            {$submitting ? 'Processing...' : 'Proceed to payment'}
        </button>
        <footer class="form__footer">
            <ul>
                <li><img src={formImage1} alt=""></li>
                <li><img src={formImage2} alt=""></li>
                <li><img src={formImage3} alt=""></li>
            </ul>
        </footer>
    </form>
</section>

<style lang="scss">

  .form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    border: 1px solid #dbdbdb;
    border-radius: 1.25rem;
    padding: 1.5rem;

    &__group {
      position: relative;
    }

    &__title {
      font-weight: 500;
      text-align: center;
      font-size: 2rem;
      line-height: 2.34375rem;
      color: var(--headings-color);
    }

    &__row {
      width: 100%;
      display: flex;
      gap: 1rem;


      > * {
        flex: 1 1 auto;
      }
    }

    &__label {
      display: none;
    }


    &__input {
      width: 100%;
      border: 1px solid #ADADAD;
      border-radius: 0.625rem;
      padding: 0.75rem 1rem;

      + p {
        font-size: 0.875rem;
        padding-left: 0.5rem;
      }

      &--invalid {
        color: red;
        border-color: red;

        &::placeholder {
          color: red;
        }

        + p {
          color: red;
        }
      }

      &:focus,
      &:active {
        color: var(--headings-color);
        border-color: var(--headings-color);
        outline: none;
      }
    }

    &__button {
      border: 1px solid var(--primary-color);
      background-color: var(--primary-color);
      color: #fff;
      padding: 0.75rem 1rem;
      border-radius: 0.625rem;
      font-weight: 600;
      text-transform: uppercase;
      cursor: pointer;
      margin-block: 0.5rem;


      &[disabled] {
        opacity: 0.7;
        cursor: not-allowed;
        filter: grayscale(1);
      }
    }

    &__footer {
      ul {
        list-style: none;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        padding: 0;
        gap: 1rem;
      }
    }
  }
</style>