<template>
  <div class="hello">
    <b-container>
      <b-navbar
        toggleable="lg"
        type="dark"
        variant="info"
      >
        <b-navbar-brand href="#">NavBar</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse
          id="nav-collapse"
          is-nav
        >
          <b-navbar-nav>
            <b-nav-item href="#">Link</b-nav-item>
            <b-nav-item
              href="#"
              disabled
            >Disabled</b-nav-item>
          </b-navbar-nav>

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-nav-form>
              <b-form-input
                size="sm"
                class="mr-sm-2"
                placeholder="Search"
              ></b-form-input>
              <b-button
                size="sm"
                class="my-2 my-sm-0"
                type="submit"
              >Search</b-button>
            </b-nav-form>

            <b-nav-item-dropdown
              text="Lang"
              right
            >
              <b-dropdown-item href="#">EN</b-dropdown-item>
              <b-dropdown-item href="#">ES</b-dropdown-item>
              <b-dropdown-item href="#">RU</b-dropdown-item>
              <b-dropdown-item href="#">FA</b-dropdown-item>
            </b-nav-item-dropdown>

            <b-nav-item-dropdown right>
              <!-- Using 'button-content' slot -->
              <template v-slot:button-content>
                <em>User</em>
              </template>
              <b-dropdown-item href="#">Profile</b-dropdown-item>
              <b-dropdown-item href="#">Sign Out</b-dropdown-item>
            </b-nav-item-dropdown>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
      <b-carousel
        id="carousel-1"
        v-model="slide"
        :interval="4000"
        controls
        indicators
        background="#ababab"
        img-width="1024"
        img-height="480"
        style="text-shadow: 1px 1px 2px #333;"
        @sliding-start="onSlideStart"
        @sliding-end="onSlideEnd"
      >
        <!-- Text slides with image -->
        <b-carousel-slide
          caption="First slide"
          text="Nulla vitae elit libero, a pharetra augue mollis interdum."
          img-src="https://picsum.photos/1024/480/?image=52"
        ></b-carousel-slide>

        <!-- Slides with custom text -->
        <b-carousel-slide img-src="https://picsum.photos/1024/480/?image=54">
          <h1>Hello world!</h1>
        </b-carousel-slide>

        <!-- Slides with image only -->
        <b-carousel-slide img-src="https://picsum.photos/1024/480/?image=58"></b-carousel-slide>

        <!-- Slides with img slot -->
        <!-- Note the classes .d-block and .img-fluid to prevent browser default image alignment -->
        <b-carousel-slide>
          <template v-slot:img>
            <img
              class="d-block img-fluid w-100"
              width="1024"
              height="480"
              src="https://picsum.photos/1024/480/?image=55"
              alt="image slot"
            >
          </template>
        </b-carousel-slide>

        <!-- Slide with blank fluid image to maintain slide aspect ratio -->
        <b-carousel-slide
          caption="Blank Image"
          img-blank
          img-alt="Blank image"
        >
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse eros felis, tincidunt
            a tincidunt eget, convallis vel est. Ut pellentesque ut lacus vel interdum.
          </p>
        </b-carousel-slide>
      </b-carousel>
      <b-card-group columns>
        <b-card
          title="Card title that wraps to a new line"
          img-src="https://placekitten.com/g/400/450"
          img-alt="Image"
          img-top
        >
          <b-card-text>
            This is a wider card with supporting text below as a natural lead-in to additional content.
            This content is a little bit longer.
          </b-card-text>
        </b-card>

        <b-card header="Quote">
          <blockquote class="blockquote mb-0">
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
            <footer class="blockquote-footer">
              Someone famous in <cite title="Source Title">Source Title</cite>
            </footer>
          </blockquote>
        </b-card>

        <b-card
          title="Title"
          img-src="https://placekitten.com/500/350"
          img-alt="Image"
          img-top
        >
          <b-card-text>
            This card has supporting text below as a natural lead-in to additional content.
          </b-card-text>
          <b-card-text class="small text-muted">Last updated 3 mins ago</b-card-text>
        </b-card>

        <b-card
          bg-variant="primary"
          text-variant="white"
        >
          <blockquote class="card-blockquote">
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
            <footer>
              <small>Someone famous in <cite title="Source Title">Source Title</cite></small>
            </footer>
          </blockquote>
        </b-card>

        <b-card>
          <b-card-title>Title</b-card-title>
          <b-card-text>
            This card has supporting text below as a natural lead-in to additional content.
          </b-card-text>
          <b-card-text class="small text-muted">Last updated 3 mins ago</b-card-text>
        </b-card>

        <b-card
          img-src="https://picsum.photos/400/400/?image=41"
          img-alt="Image"
          overlay
        ></b-card>

        <b-card
          img-src="https://picsum.photos/400/200/?image=41"
          img-alt="Image"
          img-top
        >
          <b-card-text>
            This is a wider card with supporting text below as a natural lead-in to additional content.
            This card has even longer content than the first.
          </b-card-text>
          <template v-slot:footer>
            <small class="text-muted">Footer Text</small>
          </template>
        </b-card>
      </b-card-group>
      <b-progress
        :value="value"
        :max="max"
        show-progress
        animated
      ></b-progress>
      <b-progress
        class="mt-2"
        :max="max"
        show-value
      >
        <b-progress-bar
          :value="value * (6 / 10)"
          variant="success"
        ></b-progress-bar>
        <b-progress-bar
          :value="value * (2.5 / 10)"
          variant="warning"
        ></b-progress-bar>
        <b-progress-bar
          :value="value * (1.5 / 10)"
          variant="danger"
        ></b-progress-bar>
      </b-progress>

      <b-button
        class="mt-3"
        @click="randomValue"
      >Click me</b-button>
    </b-container>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        value: 45,
        max: 100
      };
    },
    methods: {
      randomValue() {
        this.value = Math.random() * this.max;
      }
    }
  };
</script>