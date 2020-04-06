<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <nav class="navbar navbar-expand-lg">
          <a class="navbar-brand" href="/">
            <div class="media">
              <img
                class="mr-3"
                src="https://www.danhnguyen.nl/wp-content/themes/D4NH_V05/img/profile.png"
                alt="Foto van Danh"
              />
              <div class="media-body">
                <span>Danh Nguyen</span><br />
                <small>Frontend Developer</small>
              </div>
            </div>
          </a>
          <ul class="navbar-nav ml-auto">
            <li class="nav-item">
              <a class="nav-link" href="./about.html">Over mij</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="/blog.html">Blog</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="/projects.html">Projecten</a>
            </li>
          </ul>
        </nav>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
a {
  color: #444;
  &:hover {
    color: #88c441;
  }
}

.navbar {
  margin-bottom: 20px;
  padding: 0;
  height: 70px;
  border-bottom: 1px solid #e7e7e7;
}

.nav {
  &-link {
    font-size: 14px;

    // &.router-link-active {
    //   color: #88c441;
    // }
  }
}

small {
  font-size: 65%;
}

.media {
  line-height: 18px;
  margin-top: 15px;

  &-body {
    margin-top: -3px;
  }

  img {
    padding-left: 0.5rem;
    margin-top: -13px;
  }
}
</style>
