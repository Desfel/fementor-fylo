<template>
  <div class="page-wrapper">
    <div class="module-wrapper">
      <div class="left-module">
        <img class="logo" src="@/assets/img/logo.svg" alt="Fylo logo" />

        <div class="icons-wrapper">
          <span>
            <img src="@/assets/img/icon-document.svg" alt="Documents" />
          </span>
          <span>
            <img src="@/assets/img/icon-folder.svg" alt="Folders" />
          </span>
          <span>
            <img src="@/assets/img/icon-upload.svg" alt="Uploads" />
          </span>
        </div>
      </div>

      <div class="right-module">
        <div class="popup-info">
          <p>185 <span>GB left</span></p>
        </div>

        <p>You’ve used <strong>815 GB</strong> of your storage</p>

        <div class="bar-wrapper">
          <div class="progress-bar"></div>
        </div>

        <div class="sub-content">
          <p class="starter-progress">0 GB</p>
          <p class="end-progress">1000 GB</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  head() {
    return {
      title: {
        inner: 'Home'
      },
      meta: [
        {
          name: 'description',
          content: `${this.appTitle} home page`,
          id: 'desc'
        }
      ]
    }
  },
  computed: mapState('app', ['appTitle'])
}
</script>

<style lang="scss" scoped>
@import '@/theme/variables.scss';

.page-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  background: no-repeat bottom left/100% 50% url('../assets/img/bg-desktop.png'), $neutralColor4;
  min-height: 100vh;
  height: 100%;

  @media (max-width: 900px) {
    background: no-repeat top center/cover url('../assets/img/bg-mobile.png'), $neutralColor4;
  }

  .module-wrapper {
    display: flex;
    align-items: flex-end;
    width: 100%;
    padding: 0 15.5%;

    @media (max-width: 1200px) {
      padding: 0 10%;
    }

    @media (max-width: 900px) {
      flex-direction: column;
      align-items: center;
      padding: 0 25px;
    }
  }

  .right-module,
  .left-module {
    box-shadow: 0px 75px 100px -30px rgba(0, 0, 0, 0.24776);
    background: $neutralColor3;
  }

  .left-module {
    padding: 40px 133px 40px 40px;
    border-radius: 10px 100px 10px 10px;

    @media (min-width: 901px) {
      margin-right: 30px;
    }

    @media (max-width: 900px) {
      width: 100%;
      margin-bottom: 16px;
      padding-right: 0;
    }

    .logo {
      margin-bottom: 33px;
    }

    .icons-wrapper {
      display: flex;

      span {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 48px;
        height: 48px;
        border-radius: 10px;
        background: $neutralColor4;

        &:not(:last-child) {
          margin-right: 16px;
        }
      }
    }
  }

  .right-module {
    position: relative;
    padding: 40px;
    border-radius: 10px;
    flex-grow: 1;
    color: $neutralColor1;

    @media (max-width: 900px) {
      width: 100%;
    }

    .popup-info {
      position: absolute;
      top: -47px;
      right: 40px;
      padding: 16px 24px;
      background: white;
      box-shadow: 0px 75px 100px -30px rgba(0, 0, 0, 0.24776);
      border-radius: 10px 10px 0px 10px;


      @media (max-width: 900px) {
        top: auto;
        bottom: -47px;
        left: 0;
        right: 0;
        margin: auto;
        width: fit-content;
        border-radius: 10px;
      }

      &:after {
        content: '';
        display: block;
        position: absolute;
        bottom: -31px;
        right: -3px;
        border-top: 24px solid transparent;
        border-bottom: 23px solid transparent;
        border-left: 23px solid white;
        transform: rotate(-45deg);

        @media (max-width: 900px) {
          display: none;
        }
      }

      p {
        display: flex;
        align-items: center;
        color: $neutralColor4;
        font-weight: bold;
        font-size: 40px;
        line-height: 40px;

        span {
          margin-top: 5px;
          margin-left: 10px;
          font-weight: bold;
          font-size: 12px;
          line-height: 14px;
          /* identical to box height */

          text-align: right;
          letter-spacing: 1px;
          opacity: .5;
          text-transform: uppercase;
        }
      }
    }

    .bar-wrapper {
      position: relative;
      margin: 16px 0 8px;
      width: 100%;
      height: 20px;
      border-radius: 10px;
      background: rgba($neutralColor4, .5);

      .progress-bar {
        position: absolute;
        top: 3px;
        left: 3px;
        width: calc(80% - 3px);
        height: 14px;
        background: linear-gradient(90deg, $gradient1 0%, $gradient2 100%);
        border-radius: 8px;

        &:after {
          content: '';
          position: absolute;
          top: 2px;
          right: 2px;
          width: 10px;
          height: 10px;
          background: white;
          border-radius: 50%;
        }
      }
    }

    .sub-content {
      display: flex;
      width: 100%;

      p {
        font-weight: bold;
        font-size: 12px;
        line-height: 14px;
      }

      .end-progress {
        margin-left: auto;
      }
    }
  }
}
</style>
