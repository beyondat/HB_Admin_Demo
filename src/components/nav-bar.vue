<script>
import { authComputed } from '@state/helpers'
import VuePerfectScrollbar from 'vue-perfect-scrollbar'

export default {
  components: { VuePerfectScrollbar },
  props: {
    user: {
      type: Object,
      required: false,
      default: () => ({}),
    },
  },
  data() {
    return {}
  },
  computed: {
    ...authComputed,
  },
  methods: {
    toggleMenu() {
      this.$parent.toggleMenu()
    },
    toggleRightSidebar() {
      this.$parent.toggleRightSidebar()
    },
  },
}
</script>

<template>
  <!-- Topbar Start -->
  <div class="navbar-custom">
    <ul class="list-unstyled topnav-menu float-right mb-0">
      <li class="d-none d-sm-block">
        <form class="app-search">
          <div class="app-search-box">
            <div class="input-group">
              <input type="text" class="form-control" placeholder="Search..." />
              <div class="input-group-append">
                <button class="btn" type="submit">
                  <i class="fe-search"></i>
                </button>
              </div>
            </div>
          </div>
        </form>
      </li>

      <b-nav-item-dropdown right class="notification-list">
        <template slot="button-content" class="nav-link dropdown-toggle">
          <i class="fe-bell noti-icon"></i>
          <span class="badge badge-danger rounded-circle noti-icon-badge">9</span>
        </template>

        <b-dropdown-text href="#" class="dropdown-item noti-title">
          <h5 class="m-0">
            <span class="float-right">
              <a href class="text-dark">
                <small>Clear All</small>
              </a>
            </span>Notification
          </h5>
        </b-dropdown-text>

        <b-dropdown-text href="#" class="p-0">
          <VuePerfectScrollbar v-once class="noti-scroll">
            <a href="javascript:void(0);" class="dropdown-item notify-item active">
              <div class="notify-icon">
                <img src="@assets/images/users/user-1.jpg" class="img-fluid rounded-circle" alt />
              </div>
              <p class="notify-details">Cristina Pride</p>
              <p class="text-muted mb-0 user-msg">
                <small>Hi, How are you? What about our next meeting</small>
              </p>
            </a>

            <!-- item-->
            <a href="javascript:void(0);" class="dropdown-item notify-item">
              <div class="notify-icon bg-primary">
                <i class="mdi mdi-comment-account-outline"></i>
              </div>
              <p class="notify-details">
                Caleb Flakelar commented on Admin
                <small class="text-muted">1 min ago</small>
              </p>
            </a>

            <!-- item-->
            <a href="javascript:void(0);" class="dropdown-item notify-item">
              <div class="notify-icon">
                <img src="@assets/images/users/user-4.jpg" class="img-fluid rounded-circle" alt />
              </div>
              <p class="notify-details">Karen Robinson</p>
              <p class="text-muted mb-0 user-msg">
                <small>Wow ! this admin looks good and awesome design</small>
              </p>
            </a>

            <!-- item-->
            <a href="javascript:void(0);" class="dropdown-item notify-item">
              <div class="notify-icon bg-warning">
                <i class="mdi mdi-account-plus"></i>
              </div>
              <p class="notify-details">
                New user registered.
                <small class="text-muted">5 hours ago</small>
              </p>
            </a>

            <!-- item-->
            <a href="javascript:void(0);" class="dropdown-item notify-item">
              <div class="notify-icon bg-info">
                <i class="mdi mdi-comment-account-outline"></i>
              </div>
              <p class="notify-details">
                Caleb Flakelar commented on Admin
                <small class="text-muted">4 days ago</small>
              </p>
            </a>

            <!-- item-->
            <a href="javascript:void(0);" class="dropdown-item notify-item">
              <div class="notify-icon bg-secondary">
                <i class="mdi mdi-heart"></i>
              </div>
              <p class="notify-details">
                Carlos Crouch liked
                <b>Admin</b>
                <small class="text-muted">13 days ago</small>
              </p>
            </a>
          </VuePerfectScrollbar>

          <a
            href="javascript:void(0);"
            class="dropdown-item text-center text-primary notify-item notify-all"
          >
            View all
            <i class="fi-arrow-right"></i>
          </a>
        </b-dropdown-text>
      </b-nav-item-dropdown>

      <b-nav-item-dropdown right class="notification-list" menu-class="profile-dropdown">
        <template slot="button-content">
          <div class="nav-user mr-0">
            <img src="@assets/images/users/user-1.jpg" alt="user-image" class="rounded-circle" />
            <span class="pro-user-name ml-1">
              {{user ? user.name : ''}}
              <i class="mdi mdi-chevron-down"></i>
            </span>
          </div>
        </template>

        <b-dropdown-item href="#">
          <i class="fe-user mr-1"></i>
          <span>My Account</span>
        </b-dropdown-item>

        <b-dropdown-item href="#">
          <i class="fe-settings mr-1"></i>
          <span>Settings</span>
        </b-dropdown-item>

        <b-dropdown-item href="#">
          <i class="fe-lock mr-1"></i>
          <span>Lock Screen</span>
        </b-dropdown-item>

        <b-dropdown-divider></b-dropdown-divider>
        <b-dropdown-item href="/logout">
          <i class="fe-log-out mr-1"></i>
          <span>Logout</span>
        </b-dropdown-item>
      </b-nav-item-dropdown>

      <li class="dropdown notification-list">
        <button
          class="btn btn-link nav-link right-bar-toggle toggle-right"
          @click="toggleRightSidebar"
        >
          <i class="fe-settings noti-icon toggle-right"></i>
        </button>
      </li>
    </ul>

    <!-- LOGO -->
    <div class="logo-box">
      <a href="index.html" class="logo text-center">
        <span class="logo-lg">
          <img src="@assets/images/logo-light.png" alt height="18" />
          <!-- <span class="logo-lg-text-light">Xeria</span> -->
        </span>
        <span class="logo-sm">
          <!-- <span class="logo-sm-text-dark">X</span> -->
          <img src="@assets/images/logo-sm.png" alt height="24" />
        </span>
      </a>
    </div>

    <ul class="list-unstyled topnav-menu topnav-menu-left m-0">
      <li>
        <button class="button-menu-mobile" @click="toggleMenu">
          <i class="fe-menu"></i>
        </button>
      </li>

      <b-nav-item-dropdown class="d-none d-lg-block">
        <template slot="button-content">
          Create New
          <i class="mdi mdi-chevron-down"></i>
        </template>
        <b-dropdown-item href="#">
          <i class="fe-briefcase mr-1"></i>
          <span>New Projects</span>
        </b-dropdown-item>
        <b-dropdown-item href="#">
          <i class="fe-user mr-1"></i>
          <span>Create Users</span>
        </b-dropdown-item>
        <b-dropdown-item href="#">
          <i class="fe-bar-chart-line- mr-1"></i>
          <span>Revenue Report</span>
        </b-dropdown-item>
        <b-dropdown-item href="#">
          <i class="fe-settings mr-1"></i>
          <span>Settings</span>
        </b-dropdown-item>
        <b-dropdown-item href="#">
          <i class="fe-headphones mr-1"></i>
          <span>Help & Support</span>
        </b-dropdown-item>
      </b-nav-item-dropdown>
    </ul>
  </div>
  <!-- end Topbar -->
</template>

<style lang="scss">
.noti-scroll {
  height: 220px;
}
.ps > .ps__scrollbar-y-rail {
  width: 8px !important;
  background-color: transparent !important;
}
.ps > .ps__scrollbar-y-rail > .ps__scrollbar-y,
.ps.ps--in-scrolling.ps--y > .ps__scrollbar-y-rail > .ps__scrollbar-y,
.ps > .ps__scrollbar-y-rail:active > .ps__scrollbar-y,
.ps > .ps__scrollbar-y-rail:hover > .ps__scrollbar-y {
  width: 6px !important;
}
.button-menu-mobile {
  outline: none !important;
}
</style>
