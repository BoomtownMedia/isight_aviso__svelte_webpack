<script>
  import { onMount } from "svelte";
  export let pageData = {};
  let posts = [];
  let slug;
  let imageURL;

  onMount(async function() {
    const response = await fetch("https://blog-api-isight.herokuapp.com/posts");
    posts = await response.json();
    posts = posts.filter(i => window.location.pathname.includes(i.slug));
    pageData = posts[0];
    imageURL = pageData.imageBackdrop.url;
  });
</script>

<div class="super_container">

  <!-- Header -->

  <header class="header">
    <div class="container">
      <div class="row">
        <div class="col">
          <div
            class="header_content d-flex flex-row align-items-center
            justify-content-start">
            <div class="logo">
              <a href="/">Isight Blog</a>
            </div>
            <!-- <nav class="main_nav">
              <ul>
                <li class="active">
                  <a href="index.html">Home</a>
                </li>
                <li>
                  <a href="#">Fashion</a>
                </li>
                <li>
                  <a href="#">Gadgets</a>
                </li>
                <li>
                  <a href="#">Lifestyle</a>
                </li>
                <li>
                  <a href="#">Video</a>
                </li>
                <li>
                  <a href="contact.html">Contact</a>
                </li>
              </ul>
            </nav> -->
            <div class="search_container ml-auto">
              <div class="weather">
                <div class="temperature">+10°</div>
                <img class="weather_icon" src="images/cloud.png" alt="" />
              </div>
              <form action="#">
                <input
                  type="search"
                  class="header_search_input"
                  required="required"
                  placeholder="Type to Search..." />
                <img
                  class="header_search_icon"
                  src="images/search.png"
                  alt="" />
              </form>

            </div>
            <div class="hamburger ml-auto menu_mm">
              <i class="fa fa-bars trans_200 menu_mm" aria-hidden="true" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </header>

  <!-- Menu -->

  <div
    class="menu d-flex flex-column align-items-end justify-content-start
    text-right menu_mm trans_400">
    <div class="menu_close_container">
      <div class="menu_close">
        <div />
        <div />
      </div>
    </div>
    <div class="logo menu_mm">
      <a href="/">Isight Blog</a>
    </div>
    <div class="search">
      <form action="#">
        <input
          type="search"
          class="header_search_input menu_mm"
          required="required"
          placeholder="Type to Search..." />
        <img
          class="header_search_icon menu_mm"
          src="images/search_2.png"
          alt="" />
      </form>
    </div>
    <nav class="menu_nav">
      <ul>
        <li class="menu_mm">
          <a href="index.html">home</a>
        </li>
      </ul>
    </nav>
  </div>

  <!-- Home -->

  <div
    class="home"
    style="background-image: url('{imageURL}'); background-size: cover;
    background-position: center">
    <div
      class="home_background parallax-window"
      data-parallax="scroll"
      data-speed="0.8" />
    <div class="home_content">
      <div class="post_title">{pageData.title}</div>
      <div
        class="post_author d-flex flex-row align-items-center
        justify-content-center">
        <div class="post_meta">
          <a href="#">{pageData.author}</a>
          <span>
            {new Date(pageData.createdAt).toLocaleDateString('default')}
          </span>
        </div>
      </div>
    </div>
  </div>

  <!-- Page Content -->

  <div class="page_content">
    <div class="container">
      <div class="row">

        <!-- Post Content -->

        <div class="col-lg-10 offset-lg-1">
          <div class="post_content">

            <!-- Post Body -->

            <div class="post_body">
              <p class="post_p">{pageData.postBody}</p>

              <!-- Post Tags and Share-->
              <div
                class="tags_share d-flex flex-row align-items-center
                justify-content-start">
                <div class="post_share ml-sm-auto">
                  <span>share</span>
                  <ul class="post_share_list">
                    <li class="post_share_item">
                      <a href="#">
                        <i class="fa fa-facebook" aria-hidden="true" />
                      </a>
                    </li>
                    <li class="post_share_item">
                      <a href="#">
                        <i class="fa fa-twitter" aria-hidden="true" />
                      </a>
                    </li>
                    <li class="post_share_item">
                      <a href="#">
                        <i class="fa fa-google" aria-hidden="true" />
                      </a>
                    </li>
                  </ul>
                </div>
              </div>

            </div>
          </div>
        </div>

      </div>

    </div>
  </div>
  <footer class="footer">
    <div class="container">
      <div class="row row-lg-eq-height">
        <div class="col-lg-9 order-lg-1 order-2">
          <div class="footer_content">
            <div class="footer_logo">
              <a href="#">avision</a>
            </div>
            <div class="footer_social">
              <ul>
                <li class="footer_social_facebook">
                  <a href="#">
                    <i class="fa fa-facebook" aria-hidden="true" />
                  </a>
                </li>
                <li class="footer_social_twitter">
                  <a href="#">
                    <i class="fa fa-twitter" aria-hidden="true" />
                  </a>
                </li>
                <li class="footer_social_pinterest">
                  <a href="#">
                    <i class="fa fa-pinterest" aria-hidden="true" />
                  </a>
                </li>
                <li class="footer_social_vimeo">
                  <a href="#">
                    <i class="fa fa-vimeo" aria-hidden="true" />
                  </a>
                </li>
                <li class="footer_social_instagram">
                  <a href="#">
                    <i class="fa fa-instagram" aria-hidden="true" />
                  </a>
                </li>
                <li class="footer_social_google">
                  <a href="#">
                    <i class="fa fa-google" aria-hidden="true" />
                  </a>
                </li>
              </ul>
            </div>
            <div class="copyright">
              <!-- Link back to Colorlib can't be removed. Template is licensed under CC BY 3.0. -->
              Copyright &copy;
              <script>
                document.write(new Date().getFullYear());
              </script>
              All rights reserved | This template is made with
              <i class="fa fa-heart-o" aria-hidden="true" />
              by
              <a href="https://colorlib.com" target="_blank">Colorlib</a>
              <!-- Link back to Colorlib can't be removed. Template is licensed under CC BY 3.0. -->
            </div>
          </div>
        </div>
        <div class="col-lg-3 order-lg-2 order-1">
          <div class="subscribe">
            <div class="subscribe_background" />
            <div class="subscribe_content">
              <div class="subscribe_title">Subscribe</div>
              <form action="#">
                <input
                  type="email"
                  class="sub_input"
                  placeholder="Your Email"
                  required="required" />
                <button class="sub_button">
                  <svg
                    version="1.1"
                    id="link_arrow_1"
                    xmlns="http://www.w3.org/2000/svg"
                    xmlns:xlink="http://www.w3.org/1999/xlink"
                    x="0px"
                    y="0px"
                    width="19px"
                    height="13px"
                    viewBox="0 0 19 13"
                    enable-background="new 0 0 19 13"
                    xml:space="preserve">
                    <polygon
                      fill="#FFFFFF"
                      points="12.475,0 11.061,0 17.081,6.021 0,6.021 0,7.021
                      17.038,7.021 11.06,13 12.474,13 18.974,6.5 " />
                  </svg>
                </button>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </footer>
</div>
