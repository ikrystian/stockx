<script lang="ts">
    import {z} from 'zod'

    import {ZodFormStore} from "@nerd-coder/svelte-zod-form";

    const formImages: string[] = [
        'form_1.svg',
        'form_2.svg',
        'form_3.svg',
    ]

    const formSchema = z.object({
        firstName: z.string(),
        lastName: z.string(),
        street: z.string(),
        postalCode: z.string(),
        city: z.string(),
        phone: z.string(),
        email: z.string().email(),
    });
    let success = false;
    const form = new ZodFormStore(formSchema, {
        debug: true,
        onSubmit: async (values) => {
            await new Promise((r) => setTimeout(r, 2000))
            form.reset();
            alert(`Submitted values: ${JSON.stringify(values)}`);
            success = true;
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
    const {submitting, valid, model} = form

</script>

<section class="form-section">
    <form class="form" on:submit|preventDefault={form.triggerSubmit}>
        <h2 class="form__title">Enter details</h2>
        {#if success}
            <div role="alert" class="form__alert form__alert--success">
                Form sent.
            </div>
        {/if}
        <div class="form__row">
            <div class="form__group">
                <label class="form__label" for="firstName">First name</label>
                <input
                        class="form__input"
                        class:form__input--invalid={!$firstName_valid && $firstName_touched}
                        class:form__input--valid={$firstName_valid && $firstName_dirty}
                        name="firstName"
                        on:blur={form.fields.firstName.handleBlur}
                        on:input={form.fields.firstName.handleChange}
                        placeholder="First name"
                        type="text"
                        value={$firstName_value || ''}
                />
                {#if $firstName_error && $firstName_touched}<p>{$firstName_error}</p>{/if}
            </div>

            <div class="form__group">
                <label class="form__label" for="lastName">Last name</label>
                <input
                        class="form__input"
                        class:form__input--invalid={!$lastName_valid && $lastName_touched}
                        class:form__input--valid={$lastName_valid && $lastName_dirty}
                        name="lastName"
                        on:blur={form.fields.lastName.handleBlur}
                        on:input={form.fields.lastName.handleChange}
                        placeholder="Last name"
                        type="text"
                        value={$lastName_value || ''}
                />
                {#if $lastName_error && $lastName_touched}<p>{$lastName_error}</p>{/if}
            </div>

        </div>

        <div class="form__group">
            <label class="form__label" for="street">Street</label>
            <input
                    class="form__input"
                    class:form__input--invalid={!$street_valid && $street_touched}
                    class:form__input--valid={$street_valid && $street_dirty}
                    name="street"
                    on:blur={form.fields.street.handleBlur}
                    on:input={form.fields.street.handleChange}
                    placeholder="Street"
                    type="text"
                    value={$street_value || ''}
            />
            {#if $street_error && $street_touched}<p>{$street_error}</p>{/if}
        </div>

        <div class="form__row">

            <div class="form__group">
                <label class="form__label" for="postalCode">Postal code</label>
                <input
                        class="form__input"
                        class:form__input--invalid={!$postalCode_valid && $postalCode_touched}
                        class:form__input--valid={$postalCode_valid && $postalCode_dirty}
                        name="postalCode"
                        on:blur={form.fields.postalCode.handleBlur}
                        on:input={form.fields.postalCode.handleChange}
                        placeholder="Postal code"
                        type="text"
                        value={$postalCode_value || ''}
                />
                {#if $postalCode_error && $postalCode_touched}<p>{$postalCode_error}</p>{/if}
            </div>

            <div class="form__group">
                <label class="form__label" for="city">City</label>
                <input
                        class="form__input"
                        class:form__input--invalid={!$city_valid && $city_touched}
                        class:form__input--valid={$city_valid && $city_dirty}
                        name="city"
                        on:blur={form.fields.city.handleBlur}
                        on:input={form.fields.city.handleChange}
                        placeholder="City"
                        type="text"
                        value={$city_value || ''}
                />
                {#if $city_error && $city_touched}<p>{$city_error}</p>{/if}
            </div>

        </div>

        <div class="form__group">
            <label class="form__label" for="phone">Phone number</label>
            <input
                    class="form__input"
                    class:form__input--invalid={!$phone_valid && $phone_touched}
                    class:form__input--valid={$phone_valid && $phone_dirty}
                    name="phone"
                    on:blur={form.fields.phone.handleBlur}
                    on:input={form.fields.phone.handleChange}
                    placeholder="Phone number"
                    type="tel"
                    value={$phone_value || ''}
            />
            {#if $phone_error && $phone_touched}<p>{$phone_error}</p>{/if}
        </div>

        <div class="form__group">
            <label class="form__label" for="email">E-mail</label>
            <input
                    class="form__input"
                    class:form__input--invalid={!$email_valid && $email_touched}
                    class:form__input--valid={$email_valid && $email_dirty}
                    name="email"
                    on:blur={form.fields.email.handleBlur}
                    on:input={form.fields.email.handleChange}
                    placeholder="E-mail"
                    type="email"
                    value={$email_value || ''}
            />
            {#if $email_error && $email_touched}<p>{$email_error}</p>{/if}
        </div>

        <button class="form__button" disabled={!$valid || $submitting} type="submit">
            {$submitting ? 'Processing...' : 'Proceed to payment'}
        </button>
        {#if formImages.length > 0}
            <footer class="form__footer">
                <ul>
                    {#each formImages as image, index(image)}
                        <li><img alt="form image {index}" src="/assets/{image}" loading="lazy"></li>
                    {/each}
                </ul>
            </footer>
        {/if}
    </form>
</section>
<style lang="scss">
  .form-section {
    margin-top: 2rem;

    @media (width > 48rem) { // 768px / 16 = 48rem
      margin-top: 1.5rem;
    }
  }

  .form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    border: 0.0625rem solid #dbdbdb; // 1px / 16 = 0.0625rem
    border-radius: 0.78125rem; // 1.25rem = 1.25 * 16 = 20px; 20px / 16 = 1.25rem
    padding: 1.5rem;

    &__alert {
      padding: 1rem;
      border: 1px solid transparent;
      text-align: center;
      border-radius: 0.5rem;

      &--success {
        background-color: var(--primary-color);
        color: var(--invert-text);
        border-color: var(--primary-color);
      }
    }

    &__group {
      position: relative;
    }

    &__title {
      font-weight: 500;
      text-align: center;
      font-size: 2rem;
      line-height: 2.34375rem; // 2.34375rem = 37.5px / 16 = 2.34375rem
      color: var(--headings-color);
    }

    &__row {
      width: 100%;
      display: flex;
      flex-direction: column;
      gap: 1rem;

      @media (width > 33.5rem) { // 536px / 16 = 33.5rem
        flex-direction: row;
      }

      @media (width > 48rem) { // 768px / 16 = 48rem
        flex-direction: column;
      }

      @media (width > 62rem) { // 992px / 16 = 62rem
        flex-direction: row;
      }

      > * {
        flex: 1 1 auto;
      }
    }

    &__label {
      display: none;
    }

    &__input {
      width: 100%;
      border: 0.0625rem solid #ADADAD; // 1px / 16 = 0.0625rem
      border-radius: 0.625rem; // 0.625rem = 10px / 16 = 0.625rem
      padding: 0.75rem 1rem;
      transition: color 0.3s ease-in-out, border-color 0.3s ease-in-out;

      + p {
        font-size: 0.875rem;
        padding-left: 0.5rem;
      }

      &--invalid {
        color: red;
        border-color: var(--warning-color);

        &::placeholder {
          color: var(--warning-color);
        }

        + p {
          color: var(--warning-color);
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
      border: 0.0625rem solid var(--primary-color); // 1px / 16 = 0.0625rem
      background-color: var(--primary-color);
      color: var(--invert-text);
      padding: 0.75rem 1rem;
      border-radius: 0.625rem; // 0.625rem = 10px / 16 = 0.625rem
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