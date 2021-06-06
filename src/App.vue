<template>
  <div id="app" class="wrapper">
    <header class="header">
      <div class="container">
        <div class="row middle">
          <div class="col-4">
            <nav class="nav">
              <router-link to="/">Home</router-link> |
              <router-link to="/about">About</router-link>
            </nav>
          </div>
          <div class="col-4 center">
            <AppLogo></AppLogo>
          </div>
          <div class="col-4 end">
            <AppCart></AppCart>
          </div>
        </div>
      </div>
    </header>

    <div class="container">
      <router-view/>
    </div>

    <footer class="footer">
      <div class="container">
        <div class="row">
          <div class="col-4 col-offset-4 center">
            <AppLogo></AppLogo>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import AppCart from "./components/Cart.vue";
import AppLogo from "./components/Logo.vue";

export default {
  components: {
    AppCart,
    AppLogo
  },
  name: 'App'
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Work+Sans:wght@400;500;700&display=swap');

// Default

$color-default-black:             #000000;
$color-default-white:             #ffffff;

// Base

$color-black:                     #151c22;
$color-white:                     #f2f2f2;
$color-blue:                      #2c39f2;
$color-grey-1:                    #727a82;
$color-grey-2:                    #ececec;
$product-bg-image:                #e5e5e5;
$product-bg-hover:                #e5e5e5;

$font-family:                    "Work Sans", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;

// Viewports
//---------------------------------

$viewport--sm:                      320px;
$viewport--md:                      768px;
$viewport--lg:                      1024px;
$viewport--xl:                      1440px;
$viewport--xxl:                     1920px;

// Retina
//---------------------------------

$retina-dpi:                        144dpi;
$retina-dppx:                       1.5dppx;

// Normalize
//---------------------------------

*,
*::before,
*::after {
  box-sizing: border-box;
}

html {
  box-sizing: border-box;
}

html,
body {
  margin: 0;
  padding: 0;
}

body {
  width: 100%;
  height: 100%;

  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  font-family: $font-family;
  color: $color-default-black;

  background-color: $color-default-white;

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

a {
  color: $color-default-black;
  text-decoration: none;
}

img,
video {
  display: block;
  max-width: 100%;
  height: auto;
}

textarea {
  resize: none;
}

// chrome autofill background removal
// Если на проекте у инпутов используются разные цвета фонов\текста -
// удалите это из глобала и используйте локально с нужными цветами
// rgba не подойдет, сконвертируйте цвет в hex без прозрачности
// если в стилях уже используется box-shadow есть другое решение -
// задать к списку транзишенов `background-color 10000000s ease-out`
input:-webkit-autofill {
  box-shadow: inset 0 0 0 1000px $color-default-white;

  -webkit-text-fill-color: $color-default-black;
}

// firefox placeholder \ invalid fix + ios bdrs
input,
textarea {
  border-radius: 0;

  &::placeholder {
    opacity: 1;
  }

  &:invalid {
    box-shadow: none;
  }
}

select {
  border-radius: 0;
}

// ie11 X removal
input {
  &::-ms-clear,
  &::-ms-reveal {
    display: none;
  }
}

// chrome search X removal
input[type="search"]::-webkit-search-decoration,
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-results-button,
input[type="search"]::-webkit-search-results-decoration {
  appearance: none;
}

// input[number] arrows removal
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  margin: 0;

  appearance: none;
}

input[type="number"] {
  appearance: textfield;
}

// ios button \ inputs reset
select,
textarea,
input:matches([type="email"],
[type="number"],
[type="password"],
[type="search"],
[type="tel"],
[type="text"],
[type="url"]) {
  appearance: none;
}

button,
[type="button"],
[type="reset"],
[type="submit"] {
  appearance: none;
}

// Mixins
//---------------------------------

@mixin retina {
  @media (min-resolution: $retina-dpi), (min-resolution: $retina-dppx) {
    @content;
  }
}

// Desktop first
@mixin viewport--md {
  @media (min-width: $viewport--md) {
    @content;
  }
}

@mixin viewport--lg {
  @media (min-width: $viewport--lg) {
    @content;
  }
}

@mixin viewport--xl {
  @media (min-width: $viewport--xl) {
    @content;
  }
}


@mixin viewport--xxl {
  @media (min-width: $viewport--xxl) {
    @content;
  }
}

// Base
//---------------------------------

.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  clip: rect(0 0 0 0);
}

.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 15px;

  &--no-padding {
    padding: 0;
  }
}

.row {
  & {
    display: flex;
    flex: 0 1 auto;
    flex-direction: row;
    flex-wrap: wrap;
    margin-right: -15px;
    margin-left: -15px;
  }

  &.reverse {
    flex-direction: row-reverse;
  }
}

.col {
  & {
    flex-grow: 1;
    flex-basis: 0;
    max-width: 100%;
  }

  &-1,
  &-2,
  &-3,
  &-4,
  &-5,
  &-6,
  &-7,
  &-8,
  &-9,
  &-10,
  &-11,
  &-12,
  &-offset-0,
  &-offset-1,
  &-offset-2,
  &-offset-3,
  &-offset-4,
  &-offset-5,
  &-offset-6,
  &-offset-7,
  &-offset-8,
  &-offset-9,
  &-offset-10,
  &-offset-11,
  &-offset-12 {
    flex: 0 0 auto;
    padding-right: 15px;
    padding-left: 15px;
  }

  &-1 {
    flex-basis: 8.33333333%;
    max-width: 8.33333333%;
  }

  &-2 {
    flex-basis: 16.66666667%;
    max-width: 16.66666667%;
  }

  &-3 {
    flex-basis: 25%;
    max-width: 25%;
  }

  &-4 {
    flex-basis: 33.33333333%;
    max-width: 33.33333333%;
  }

  &-5 {
    flex-basis: 41.66666667%;
    max-width: 41.66666667%;
  }

  &-6 {
    flex-basis: 50%;
    max-width: 50%;
  }

  &-7 {
    flex-basis: 58.33333333%;
    max-width: 58.33333333%;
  }

  &-8 {
    flex-basis: 66.66666667%;
    max-width: 66.66666667%;
  }

  &-9 {
    flex-basis: 75%;
    max-width: 75%;
  }

  &-10 {
    flex-basis: 83.33333333%;
    max-width: 83.33333333%;
  }

  &-11 {
    flex-basis: 91.66666667%;
    max-width: 91.66666667%;
  }

  &-12 {
    flex-basis: 100%;
    max-width: 100%;
  }

  &-offset-0 {
    margin-left: 0;
  }

  &-offset-1 {
    margin-left: 8.33333333%;
  }

  &-offset-2 {
    margin-left: 16.66666667%;
  }

  &-offset-3 {
    margin-left: 25%;
  }

  &-offset-4 {
    margin-left: 33.33333333%;
  }

  &-offset-5 {
    margin-left: 41.66666667%;
  }

  &-offset-6 {
    margin-left: 50%;
  }

  &-offset-7 {
    margin-left: 58.33333333%;
  }

  &-offset-8 {
    margin-left: 66.66666667%;
  }

  &-offset-9 {
    margin-left: 75%;
  }

  &-offset-10 {
    margin-left: 83.33333333%;
  }

  &-offset-11 {
    margin-left: 91.66666667%;
  }
}

.start {
  justify-content: flex-start;
  text-align: start;
}

.center {
  justify-content: center;
  text-align: center;
}

.end {
  justify-content: flex-end;
  text-align: end;
}

.top {
  align-items: flex-start;
}

.middle {
  align-items: center;
}

.bottom {
  align-items: flex-end;
}

.around {
  justify-content: space-around;
}

.between {
  justify-content: space-between;
}

.wrapper {
  & {
    position: relative;
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    overflow-x: hidden;
  }

  &--no-scrollbar {
    & {
      height: 100vh;
      height: calc(100 * var(--vh, 1vh));
      -ms-overflow-style: none;
      scrollbar-width: none;
    }

    &::-webkit-scrollbar {
      display: none;
    }
  }

  .header {
    flex-shrink: 0;
  }

  .footer {
    flex-shrink: 0;
    margin-top: auto;
  }

  main {
    flex-grow: 1;
  }
}

.scroll-lock {
  position: fixed;
  overflow-y: auto;
}

.aside {
  margin-top: 35px;
  margin-bottom: 50px;
}

.content {
  margin: 50px 0 100px;
}

// Custom checkbox
//---------------------------------
.custom-checkbox {
  & {
    font-weight: 500;
    font-size: 14px;
    line-height: 1.4;
  }

  .text {
    & {
      position: relative;
      display: block;
      padding-left: 25px;
      color: $color-grey-1;
    }

    &:before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      display: block;
      width: 20px;
      height: 20px;
      border: 2px solid $color-black;
    }
  }

  input[type="checkbox"]:focus ~ .text:before,
  input[type="checkbox"]:hover ~ .text:before {
    background-color: $color-grey-2;
  }

  input[type="checkbox"]:checked ~ .text:before {
    background-image: url("data:image/svg+xml,%3Csvg aria-hidden='true' data-prefix='fas' data-icon='check' xmlns='http://www.w3.org/2000/svg' viewBox='0 0 512 512' class='svg-inline--fa fa-check fa-w-16 fa-9x'%3E%3Cpath fill='currentColor' d='M173.898 439.404l-166.4-166.4c-9.997-9.997-9.997-26.206 0-36.204l36.203-36.204c9.997-9.998 26.207-9.998 36.204 0L192 312.69 432.095 72.596c9.997-9.997 26.207-9.997 36.204 0l36.203 36.204c9.997 9.997 9.997 26.206 0 36.204l-294.4 294.401c-9.998 9.997-26.207 9.997-36.204-.001z'/%3E%3C/svg%3E");
    background-size: 75% auto;
    background-repeat: no-repeat;
    background-position: center top 2px;
  }
}

// Header
//---------------------------------
.logo {
  display: inline-block;
  line-height: 1;
}

// Header
//---------------------------------
.header {
  & {
    padding: 10px 0 5px;
  }

  .nav {
    font-weight: 500;
  }
}

// Footer
//---------------------------------
.footer {
  & {
    padding: 10px 0 5px;
    background-color: $color-black;
  }

  .logo {
    filter: drop-shadow(0 0 2px $color-white);
  }
}

// Cart
//---------------------------------
.cart {
  & {
    position: relative;
    display: inline-block;
    padding: 5px 15px;
  }

  .count {
    position: absolute;
    top: 0;
    right: 0;
    display: block;
    padding: 2px 5px;
    font-weight: 700;
    font-size: 10px;
    line-height: 1;
    background-color: $color-default-white;
    border: 1px solid $color-black;
    border-radius: 5px;
  }
}

// Sort
//---------------------------------
.sort {
  & {
    position: relative;
    margin-left: auto;
    width: 100%;

    @include viewport--md {
      width: calc(100% / 3 - 15px);
    }

    @include viewport--lg {
      width: calc(100% / 4 - 15px);
    }
  }

  .btn {
    max-width: 100%;
    width: 100%;
  }

  .dropdown {
    & {
      position: absolute;
      right: 0;
      left: 0;
      bottom: 0;
      z-index: 100;
      transform: translateY(calc(100% + 1px));
      height: 0;
      overflow: hidden;
      background-color: $color-default-white;
    }

    &._show {
      height: auto;
    }
  }

  .items {
    & {
      margin: 0;
      padding: 10px 15px 15px;
      list-style: none;
      border: 2px solid $color-black;
      border-top: none;
    }

    > *:not(:last-of-type) {
      margin-bottom: 15px;
    }
  }
}

// Footer
//---------------------------------
.btn {
  & {
    display: block;
    padding: 18px 15px;
    font-weight: 500;
    font-size: 18px;
    line-height: 1.15;
    color: $color-white;
    background-color: $color-black;
    border: 2px solid $color-black;
    cursor: pointer;

    @include viewport--md {
      font-size: 16px;
    }
  }

  &.-toggle {
    & {
      padding-right: 55px;
      background-image: url("data:image/svg+xml,%3Csvg width='18' height='11' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1 1l8 8 8-8' stroke='%23151C22' stroke-width='2'/%3E%3C/svg%3E");
      background-size: 20px auto;
      background-repeat: no-repeat;
      background-position: right 20px center;
    }

    &._show {
      background-image: url("data:image/svg+xml,%3Csvg width='18' height='11' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M17 10L9 2l-8 8' stroke='%23151C22' stroke-width='2'/%3E%3C/svg%3E");
    }
  }

  &.-void {
    color: $color-black;
    background-color: transparent;
  }
}

// Catalog
//---------------------------------
.product-grid {
  & {
    display: grid;
    grid-template-columns: repeat(2, minmax(130px, 1fr));
    grid-gap: 30px;
    padding: 0;
    list-style: none;

    @include viewport--md {
      grid-template-columns: repeat(3, minmax(200px, 1fr));
    }

    @include viewport--lg {
      grid-template-columns: repeat(4, minmax(200px, 1fr));
    }
  }

  & > *:nth-of-type(5) {
    @media (max-width: $viewport--md - 1) {
      grid-column: span 2;
      grid-row: span 2;
    }

    @media (min-width: $viewport--md) and (max-width: $viewport--lg - 1) {
      grid-column-start: 2;
      grid-column-end: 4;
      grid-row-start: 2;
      grid-row-end: 4;
    }
  }

  & > *:nth-of-type(9n + 9) {
    @include viewport--lg {
      grid-column-start: 3;
      grid-column-end: 5;
      grid-row-start: 2;
      grid-row-end: 4;
    }
  }
}

// Product
//---------------------------------
.product {
  & {
    transition: all 0.25s ease;
  }

  &,
  &-inner {
    position: relative;
    display: flex;
    flex-direction: column;
    flex: 1 0 auto;
    min-height: 100%;
  }

  .image-wrap {
    flex: 1 0 auto;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .title {
    margin-top: 15px;
    margin-bottom: 10px;
    font-weight: 500;
    font-size: 16px;
    line-height: 1.2;

    @include viewport--lg {
      margin-top: 25px;
      margin-bottom: 15px;
      font-size: 18px;
    }
  }

  .price {
    margin-bottom: 10px;
    font-weight: 700;
    font-size: 14px;
    line-height: 1.2;
  }

  .box {
    position: relative;
    z-index: 10;

    @media (max-width: $viewport--lg - 1) {
      display: flex;

      .inner {
        width: calc(100% - 35px);
        padding-right: 10px;
      }

      .btn {
        margin-top: 15px;
        width: 35px;
        height: 35px;
        padding: 15px;
        font-size: 0;
        background-image: url("data:image/svg+xml,%3Csvg width='20' height='18' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1 1h3.273l2.192 10.202c.075.35.28.666.58.89.299.224.673.343 1.057.337h7.953c.384.006.758-.113 1.057-.337.3-.224.504-.54.579-.89L19 4.81H5.09m3.274 11.428c0 .42-.367.762-.819.762-.451 0-.818-.341-.818-.762 0-.42.367-.762.818-.762.452 0 .819.341.819.762zm9 0c0 .42-.367.762-.819.762-.451 0-.818-.341-.818-.762 0-.42.367-.762.819-.762.451 0 .818.341.818.762z' stroke='%23FFF' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E");
        background-repeat: no-repeat;
        background-position: center;
        background-size: 55% auto;
      }
    }
  }

  .dropdown {
    @include viewport--lg {
      position: absolute;
      right: -15px;
      bottom: 0;
      left: -15px;
      transform: translateY(100%);
      height: 0;
      background-color: $color-grey-2;
      overflow: hidden;
    }
  }

  &:hover .dropdown,
  &:focus-within .dropdown {
    @include viewport--lg {
      height: auto;
      padding: 15px;
    }
  }

  &:hover:before,
  &:focus-within:before {
    @include viewport--lg {
      content: '';
      position: absolute;
      top: -15px;
      right: -15px;
      bottom: -15px;
      left: -15px;
      z-index: -1;
      height: auto;
      background-color: $color-grey-2;
    }
  }
}
</style>