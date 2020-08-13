<template>
  <div id="app">
    <div class="form">
      <form @submit.prevent="submitHandler">
        <h2>Ваши данные</h2>
        <label>
          <span>Фамилия*</span>
          <input
            v-model.trim="lastname"
            type="text"
            :class="{ invalid: this.$v.lastname.$dirty && !this.$v.lastname.required }"
          />
          <span class="error" v-if="this.$v.lastname.$dirty && !this.$v.lastname.required"
            >Введите фамилию</span
          >
        </label>
        <label>
          <span>Имя*</span>
          <input
            v-model.trim="firstname"
            type="text"
            :class="{ invalid: this.$v.firstname.$dirty && !this.$v.lastname.required }"
          />
          <span class="error" v-if="this.$v.firstname.$dirty && !this.$v.firstname.required"
            >Введите имя</span
          >
        </label>
        <label>
          <span>Отчество</span>
          <input v-model.trim="middlename" type="text" />
        </label>
        <label>
          <span>Дата рождения*</span>
          <input
            v-model="birthday"
            type="date"
            :class="{
              invalid:
                this.$v.birthday.$dirty &&
                (!this.$v.birthday.required ||
                  !this.$v.birthday.minValue ||
                  !this.$v.birthday.maxValue),
            }"
          />
          <span
            class="error"
            v-if="
              this.$v.birthday.$dirty &&
                (!this.$v.birthday.required ||
                  !this.$v.birthday.minValue ||
                  !this.$v.birthday.maxValue)
            "
            >Некорректная дата</span
          >
        </label>
        <label>
          <span>Номер телефона*</span>
          <input
            v-model.trim="phone"
            type="text"
            :class="{
              invalid:
                this.$v.phone.$dirty &&
                (!this.$v.phone.required || !this.$v.phone.minLength || !this.$v.phone.maxLength),
            }"
            @keypress="pressPhoneHandler"
          />
          <span
            class="error"
            v-if="
              this.$v.phone.$dirty &&
                (!this.$v.phone.required || !this.$v.phone.minLength || !this.$v.phone.maxLength)
            "
            >Некорректный номер телефона</span
          >
        </label>
        <label>
          <span>Пол</span>
          <select v-model="gender">
            <option value="">Не выбран</option>
            <option value="male">Мужской</option>
            <option value="female">Женский</option>
          </select>
        </label>
        <label>
          <span>Группа клиентов*</span>
          <select
            multiple
            size="3"
            v-model="clients"
            :class="{
              invalid: this.$v.clients.$dirty && !this.$v.clients.required,
            }"
          >
            <option value="vip">VIP</option>
            <option value="trouble">Проблемные</option>
            <option value="OMS">ОМС</option>
          </select>
          <span class="error" v-if="this.$v.clients.$dirty && !this.$v.clients.required"
            >Выберите группу клиентов</span
          >
        </label>
        <label>
          <span>Лечащий врач</span>
          <select v-model="doctor">
            <option value="">Не выбран</option>
            <option value="1">Иванов</option>
            <option value="2">Захаров</option>
            <option value="3">Чернышева</option>
          </select>
        </label>
        <label class="checkbox">
          <input v-model="sendSms" type="checkbox" />
          <span>Не отправлять СМС</span>
        </label>
        <hr />
        <h2>Адрес</h2>
        <label>
          <span>Индекс</span>
          <input
            type="text"
            @keypress="pressDigitHandler"
            v-model="postCode"
            minlength="6"
            maxlength="6"
          />
        </label>
        <label>
          <span>Страна</span>
          <input type="text" v-model="country" />
        </label>
        <label>
          <span>Область</span>
          <input type="text" v-model="region" />
        </label>
        <label>
          <span>Город*</span>
          <input
            type="text"
            v-model="city"
            :class="{
              invalid: this.$v.city.$dirty && !this.$v.city.required,
            }"
          />
          <span class="error" v-if="this.$v.city.$dirty && !this.$v.city.required"
            >Введите город</span
          >
        </label>
        <label>
          <span>Улица</span>
          <input type="text" v-model="street" />
        </label>
        <label>
          <span>Дом</span>
          <input type="text" v-model="houseNumber" />
        </label>
        <hr />
        <h2>Паспорт</h2>
        <label>
          <span>Тип документа*</span>
          <select
            v-model="documentType"
            :class="{
              invalid: this.$v.documentType.$dirty && !this.$v.documentType.required,
            }"
          >
            <option value="">Не выбран</option>
            <option value="1">Паспорт</option>
            <option value="2">Свидетельство о рождении</option>
            <option value="3">Вод. удостоверение</option>
          </select>
          <span class="error" v-if="this.$v.documentType.$dirty && !this.$v.documentType.required"
            >Выберите тип документа</span
          >
        </label>
        <label>
          <span>Серия</span>
          <input
            type="text"
            v-model="documentSerial"
            @keypress="pressDigitHandler"
            maxlength="4"
            minlength="4"
          />
        </label>
        <label>
          <span>Номер</span>
          <input
            type="text"
            v-model="documentNumber"
            @keypress="pressDigitHandler"
            maxlength="6"
            minlength="6"
          />
        </label>
        <label>
          <span>Кем выдан</span>
          <input type="text" v-model="documentFrom" />
        </label>
        <label>
          <span>Дата выдачи*</span>
          <input
            type="date"
            v-model="documentDate"
            :class="{
              invalid:
                this.$v.documentDate.$dirty &&
                (!this.$v.documentDate.required ||
                  !this.$v.documentDate.minValue ||
                  !this.$v.documentDate.maxValue),
            }"
          />
          <span
            class="error"
            v-if="
              this.$v.documentDate.$dirty &&
                (!this.$v.documentDate.required ||
                  !this.$v.documentDate.minValue ||
                  !this.$v.documentDate.maxValue)
            "
            >Некорректная дата</span
          >
        </label>
        <button type="submit">Отправить</button>
      </form>
    </div>
  </div>
</template>

<script>
import { required, minLength, maxLength } from 'vuelidate/lib/validators'

export default {
  data: () => ({
    firstname: '',
    lastname: '',
    middlename: '',
    birthday: '',
    phone: '+7',
    gender: '',
    clients: [],
    doctor: '',
    sendSms: false,
    postCode: '',
    country: '',
    region: '',
    city: '',
    street: '',
    houseNumber: '',
    documentType: '',
    documentSerial: '',
    documentNumber: '',
    documentFrom: '',
    documentDate: '',
  }),
  watch: {
    phone() {
      if (!this.phone.startsWith('+')) this.phone = '+' + this.phone.replace('+', '')
      if (!this.phone.startsWith('+7')) this.phone = '+7' + this.phone.replace('+', '')
    },
    birthday() {
      if (new Date(this.birthday) > new Date())
        this.birthday = new Date().toISOString().slice(0, 10)
    },
    documentDate() {
      console.log(this.documentDate)
      if (new Date(this.documentDate) > new Date())
        this.documentDate = new Date().toISOString().slice(0, 10)
    },
  },
  validations: {
    firstname: { required },
    lastname: { required },
    birthday: {
      required,
      minValue: value => value > new Date(1800, 0, 1).toISOString(),
      maxValue: value => value < new Date().toISOString(),
    },
    phone: { required, minLength: minLength(12), maxLength: maxLength(12) },
    clients: { required },
    city: { required },
    documentType: { required },
    documentDate: {
      required,
      minValue: value => value > new Date(1800, 0, 1).toISOString(),
      maxValue: value => value < new Date().toISOString(),
    },
  },
  methods: {
    submitHandler() {
      if (this.$v.$invalid) {
        this.$v.$touch()
        alert('Проверьте форму на ошибки')
        return
      }
      alert('Новый клиент успешно создан')
    },
    pressPhoneHandler(e) {
      if (e.code.slice(0, 5) !== 'Digit' || this.phone.length >= 12) {
        e.preventDefault()
      }
    },
    pressDigitHandler(e) {
      if (e.code.slice(0, 5) !== 'Digit') {
        e.preventDefault()
      }
    },
  },
}
</script>

<style lang="sass">
@import 'assets/sass/index'

.form
  box-shadow: 0 5px 15px rgba(0,0,0,.5)
  max-width: 600px
  margin: 60px auto
  padding: 20px
  border-radius: 6px
  form
    display: flex
    flex-direction: column
    button
      padding: 10px 0
      cursor: pointer
      text-transform: uppercase
      background-color: #d7b5a1
      color: #fff
      border: 5px solid #fff8f4
      font-size: 18px
    button:focus
      outline: none
    hr
      width: 100%
      border: none
      border-top: 1px solid rgba(0,0,0,.1)
      margin: 20px 0
    h2
      color: #414141
      letter-spacing: .6px
      margin: 0 0 4px
    label
      padding: 5px 0
      width: 100%
      span
        color: #414141
        padding: 0 10px
        font-size: 15px
      span.error
        color: #fc7878
        font-size: 14px
      input, select
        width: calc(100% - 22px)
        border: 1px solid #ccc
        border-radius: 3px
        padding: 5px 10px
        margin: 1px 0
        transition: border .2s
      input:focus
        outline: none
      input.invalid, select.invalid
        border: 1px solid #fc7878
      select
        width: 100%
      select:focus
        outline: none
      select[multiple]
        overflow: hidden
    label.checkbox
      input
        width: auto
</style>
