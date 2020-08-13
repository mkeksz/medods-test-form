<template>
  <div id="app">
    <div class="form">
      <form>
        <h2>Ваши данные</h2>
        <label>
          <span>Фамилия*</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Имя*</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Отчество</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Дата рождения*</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Номер телефона*</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Пол</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Группа клиентов*</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Лечащий врач</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label class="checkbox">
          <input type="checkbox" />
          <span>Не отправлять СМС</span>
        </label>
        <hr />
        <h2>Адрес</h2>
        <label>
          <span>Индекс</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Страна</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Область</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Город*</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Улица</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Дом</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <hr />
        <h2>Паспорт</h2>
        <label>
          <span>Тип документа*</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Серия</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Номер</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Кем выдан</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
        <label>
          <span>Дата выдачи*</span>
          <input type="text" />
          <span class="error">ошибка</span>
        </label>
      </form>
    </div>
  </div>
</template>

<script>
export default {}
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
        visibility: hidden
      span.error.show
        visibility: visible
      input
        width: calc(100% - 20px)
        border: 1px solid #ccc
        border-radius: 3px
        padding: 5px 10px
        margin: 1px 0
      input:focus
        outline: none
    label.checkbox
      input
        width: auto
</style>
