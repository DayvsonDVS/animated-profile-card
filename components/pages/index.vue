<template>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.1/css/all.min.css"
    integrity="sha512-MV7K8+y+gLIBoVD59lQIYicR65iaqukzvf/nwasF0nqhPay5w/9lJmVM2hMDcnK1OnMGCdVK+iQrJ7lzPJQd1w=="
    crossorigin="anonymous"
    referrerpolicy="no-referrer"
  />

  <div :class="['card', { active: state }]">
    <div class="user">
      <div class="imgBx">
        <img src="@/profile.png" />
      </div>

      <div class="content">
        <h2>
          Dayvson Silvino
          <br />
          <span>Front-end</span>
        </h2>
      </div>

      <span class="toggle" @click="toogleClick"></span>
    </div>

    <ul class="contact">
      <li
        v-for="{ color, email, icon, index } in list"
        :style="`--clr:${color}; --i:${index}`"
      >
        <a href="#">
          <div class="iconBx">
            <i :class="`${icon}`"></i>
          </div>
          <p>{{ email }}</p>
        </a>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import 'assets/scss/main.scss'

const state = ref<boolean>(false)
const list = [
  {
    color: '#c71610',
    email: 'dayvson@gmail.com',
    icon: 'fa-solid fa-envelope',
    index: '1'
  },
  {
    color: '#171515',
    email: 'github/@dayvson',
    icon: 'fa-brands fa-github',
    index: '2'
  },
  {
    color: '#0a66c2',
    email: 'linkedin/@dayvson',
    icon: 'fa-brands fa-linkedin-in',
    index: '3'
  }
]

function toogleClick() {
  state.value = !state.value
}
</script>

<style scoped lang="scss">
.card {
  position: relative;
  transition: 0.5s;
  height: 100px;
  transition-delay: 0.5s;
  .contact {
    position: relative;
    top: 30px;
    width: 100%;
    height: 0;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    gap: 10px;
    transition: 0.5s;
    li {
      list-style: none;
      width: 100%;
      min-height: 100px;
      background: #fff;
      border-radius: 10px;
      display: flex;
      transition: 0.5s;
      opacity: 0;
      transform: scale(0);
      padding: 10px 30px;
      a {
        display: flex;
        align-items: center;
        text-decoration: none;
        gap: 10px;
        &:hover p {
          color: #111;
        }
        p {
          color: #666;
          font-size: 1.1em;
        }
        .iconBx {
          position: relative;
          width: 60px;
          height: 60px;
          background: var(--clr);
          border-radius: 50%;
          display: flex;
          justify-content: center;
          align-items: center;
          i {
            color: #fff;
            font-size: 1.5em;
          }
        }
      }
    }
  }
  &.active {
    height: 450px;
    transition-delay: 0s;
    .contact {
      height: 325px;
      &:hover li {
        opacity: 0.15;
        filter: blur(2px);
        transition-delay: 0s;
      }
      li {
        opacity: 1;
        transform: scale(1);
        transition-delay: calc(0.25s * var(--i));
        &:hover {
          opacity: 1;
          filter: blur(0px);
        }
      }
    }
    .user {
      .toggle {
        background: #ff4383;
        color: #fff;
        &::before {
          content: 'Close';
        }
      }
    }
  }
  .user {
    position: relative;
    width: 400px;
    min-height: 150px;
    background: #2196f3;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    gap: 10px;
    border-radius: 10px;
    padding: 60px 40px 30px;
    .toggle {
      position: absolute;
      bottom: 0;
      width: 120px;
      padding: 5px;
      background: #fff;
      border-radius: 30px;
      transform: translateY(50%);
      border: 6px solid var(--bg);
      text-align: center;
      cursor: pointer;
      font-weight: 500;
      transition: 0.5s;
      &::before {
        content: 'Contact me';
      }
    }
    .content {
      position: relative;
      text-align: center;
      h2 {
        font-size: 1.2em;
        line-height: 1.05em;
        font-weight: 600;
        color: #fff;
        span {
          font-size: 0.75em;
          font-weight: 400;
        }
      }
    }
    .imgBx {
      position: absolute;
      top: 0;
      transform: translateY(-50%);
      width: 100px;
      height: 100px;
      border-radius: 50%;
      border: 6px solid #fff;
      overflow: hidden;
      transition: 0.5s;
      z-index: 10;
      img {
        position: absolute;
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }
  }
}
</style>
