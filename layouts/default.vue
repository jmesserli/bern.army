<template>
  <div>
    <b-navbar toggleable="lg" type="light" variant="light" class="mb-3">
      <div class="container">
        <n-link to="/" tag="b-navbar-brand">
          bern.army
        </n-link>

        <b-navbar-toggle target="nav-collapse" />

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <n-link to="/timeout" tag="b-nav-item" active-class="active">
              Time out
            </n-link>
            <n-link to="/rs" tag="b-nav-item" active-class="active">
              RS Woche
            </n-link>
          </b-navbar-nav>
        </b-collapse>
      </div>
    </b-navbar>

    <nuxt />
  </div>
</template>
