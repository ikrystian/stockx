<section class="form-section">
    <h2 class="form-section__title">Enter details</h2>
    <form action="" class="form">
        <div class="form__row">
            <div class="form__group">
                <label class="form__label" for="firstName">First name</label>
                <input type="text" id="firstName" value="First name" placeholder="First name" class="form__input"
                       name="firstName"/>
            </div>

            <div class="form__group">
                <label class="form__label" for="lastName">Last name</label>
                <input type="text" id="lastName" placeholder="Last name" class="form__input" name="lastName"/>
            </div>

        </div>
        <div class="form__group">
            <label class="form__label" for="street">Street</label>
            <input type="text" id="street" placeholder="Street" class="form__input" name="street"/>
        </div>
        <div class="form__row">
            <div class="form__group">
                <label class="form__label" for="postalCode">Postal code</label>
                <input type="text" id="postalCode" placeholder="Postal code" class="form__input" name="postalCode"/>
            </div>

            <div class="form__group">
                <label class="form__label" for="city">City</label>
                <input type="text" id="city" placeholder="City" class="form__input" name="city"/>
            </div>
        </div>

        <div class="form__group">
            <label class="form__label" for="phoneNumber">Phone number</label>
            <input type="tel" id="phoneNumber" placeholder="Phone number" class="form__input" name="phoneNumber"/>
        </div>

        <div class="form__group">
            <label class="form__label" for="email">E-mail</label>
            <input type="email" id="email" placeholder="E-mail" class="form__input" name="email"/>
        </div>

        <button class="form__button">Proceed to payment</button>
        <span>IMAGE HERE</span>
    </form>
</section>

<style lang="scss">
  .form-section {
    &__title {
      font-weight: 500;
      text-align: center;
      font-size: 2rem;
      line-height: 2.34375rem;
      color: var(--headings-color);
    }
  }

  .form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    border: 1px solid #dbdbdb;
    border-radius: 1.25rem;
    padding: 1.5rem;

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
      margin-top: 0.5rem;
    }
  }
</style>