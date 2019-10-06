<script>
  import { onMount } from "svelte";

  import Header from "../components/Header.svelte";
  let posts = [];
  let videos = [];

  $: posts = posts.reverse();

  let title;
  let firstPostSlug;
  let firstPostTitle;
  let firstPostURL;
  let firstPostCategory;
  let secondPostSlug;
  let secondPostTitle;
  let secondPostURL;
  let secondPostCategory;
  let thirdPostSlug;
  let thirdPostTitle;
  let thirdPostURL;
  let thirdPostCategory;

  onMount(async function preload() {
    const response = await fetch("https://blog-api-isight.herokuapp.com/posts");
    $: posts = await response.json();
    $: firstPostSlug = posts[0].slug;
    $: firstPostTitle = posts[0].title;
    $: firstPostURL = posts[0].imageBackdrop.url;
    $: firstPostCategory = posts[0].category;
    $: secondPostSlug = posts[1].slug;
    $: secondPostTitle = posts[1].title;
    $: secondPostURL = posts[1].imageBackdrop.url;
    $: secondPostCategory = posts[1].category;
    $: thirdPostSlug = posts[2].slug;
    $: thirdPostTitle = posts[2].title;
    $: thirdPostURL = posts[2].imageBackdrop.url;
    $: thirdPostCategory = posts[2].category;

    const rez = await fetch("https://blog-api-isight.herokuapp.com/videos");
    $: videos = await rez.json();
  });

</script>

<style>
</style>

<svelte:head>
  <title>Isight Blog</title>
</svelte:head>
<Header />
<!-- Menu -->
<div class="super-container">
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
  <!-- <nav class="menu_nav">
      <ul class="menu_mm">
        <li class="menu_mm">
          <a href="index.html">home</a>
        </li>
        <li class="menu_mm">
          <a href="">test</a>
        </li>
        <li class="menu_mm">
          <a href="">Gadgets</a>
        </li>
        <li class="menu_mm">
          <a href="">Lifestyle</a>
        </li>
        <li class="menu_mm">
          <a href="">Video</a>
        </li>
        <li class="menu_mm">
          <a href="contact.html">Contact</a>
        </li>
      </ul>
    </nav> -->
</div>

<!-- Home -->

<div class="home">

  <!-- Home Slider -->

  <div class="home_slider_container" style="background-color: transparent">
    <div class="owl-carousel owl-theme home_slider">

      <!-- Slider Item -->
      <div class="owl-item">
        <div
          class="home_slider_background"
          style="background-image:url('{firstPostURL}')" />
        <div class="home_slider_content_container">
          <div class="container">
            <div class="row">
              <div class="col">
                <div class="home_slider_content">
                  <div class="home_slider_item_title">
                    <a href="blog/{firstPostSlug}">{firstPostTitle}</a>
                  </div>
                  <div class="home_slider_item_link">
                    <a href="blog/{firstPostSlug}" class="trans_200">
                      Continue Reading
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
                    </a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Similar Posts -->
        <div class="similar_posts_container">
          <div class="container">
            <div class="row d-flex flex-row align-items-end">

              <!-- Similar Post -->
              <div class="col-lg-3 col-md-6 similar_post_col">
                <div class="similar_post trans_200">
                  <a href="blog/{firstPostSlug}">{firstPostTitle}</a>
                </div>
              </div>

              <!-- Similar Post -->
              <div class="col-lg-3 col-md-6 similar_post_col">
                <div class="similar_post trans_200">
                  <a href="blog/{secondPostSlug}">{secondPostTitle}</a>
                </div>
              </div>

              <!-- Similar Post -->
              <div class="col-lg-3 col-md-6 similar_post_col">
                <div class="similar_post trans_200">
                  <a href="blog/{thirdPostSlug}">{thirdPostTitle}</a>
                </div>
              </div>

            </div>
          </div>

          <div class="home_slider_next_container">
            <div
              class="home_slider_next"
              style="background-image:url('{secondPostURL}'); background-size:
              cover">
              <div class="home_slider_next_background trans_400" />
              <div class="home_slider_next_content trans_400">
                <div class="home_slider_next_title">next</div>
                <div class="home_slider_next_link">{secondPostTitle}</div>
              </div>
            </div>
          </div>

        </div>
      </div>

      <!-- Slider Item -->
      <div class="owl-item">
        <div
          class="home_slider_background"
          style="background-image:url('{secondPostURL}')" />
        <div class="home_slider_content_container">
          <div class="container">
            <div class="row">
              <div class="col">
                <div class="home_slider_content">
                  <div class="home_slider_item_title">
                    <a href="blog/{secondPostSlug}">{secondPostTitle}</a>
                  </div>
                  <div class="home_slider_item_link">
                    <a href="blog/{secondPostSlug}" class="trans_200">
                      Continue Reading
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
                    </a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Similar Posts -->
        <div class="similar_posts_container">
          <div class="container">
            <div class="row d-flex flex-row align-items-end">

              <!-- Similar Post -->
              <div class="col-lg-3 col-md-6 similar_post_col">
                <div class="similar_post trans_200">
                  <a href="blog/{firstPostSlug}">{firstPostTitle}</a>
                </div>
              </div>

              <!-- Similar Post -->
              <div class="col-lg-3 col-md-6 similar_post_col">
                <div class="similar_post trans_200">
                  <a href="blog/{secondPostSlug}">{secondPostTitle}</a>
                </div>
              </div>

              <!-- Similar Post -->
              <div class="col-lg-3 col-md-6 similar_post_col">
                <div class="similar_post trans_200">
                  <a href="blog/{thirdPostSlug}">{thirdPostTitle}</a>
                </div>
              </div>

            </div>
          </div>

          <div class="home_slider_next_container">
            <div
              class="home_slider_next"
              style="background-image:url('{thirdPostURL}')">
              <div class="home_slider_next_background trans_400" />
              <div class="home_slider_next_content trans_400">
                <div class="home_slider_next_title">next</div>
                <div class="home_slider_next_link">{thirdPostTitle}</div>
              </div>
            </div>
          </div>

        </div>
      </div>

      <!-- Slider Item -->
      <div class="owl-item">
        <div
          class="home_slider_background"
          style="background-image:url('{thirdPostURL}')" />
        <div class="home_slider_content_container">
          <div class="container">
            <div class="row">
              <div class="col">
                <div class="home_slider_content">
                  <div class="home_slider_item_title">
                    <a href="blog/{thirdPostSlug}">{thirdPostTitle}</a>
                  </div>
                  <div class="home_slider_item_link">
                    <a href="blog/{thirdPostSlug}" class="trans_200">
                      Continue Reading
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
                    </a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Similar Posts -->
        <div class="similar_posts_container">
          <div class="container">
            <div class="row d-flex flex-row align-items-end">

              <!-- Similar Post -->
              <div class="col-lg-3 col-md-6 similar_post_col">
                <div class="similar_post trans_200">
                  <a href="blog/{firstPostSlug}">{firstPostTitle}</a>
                </div>
              </div>

              <!-- Similar Post -->
              <div class="col-lg-3 col-md-6 similar_post_col">
                <div class="similar_post trans_200">
                  <a href="blog/{secondPostSlug}">{secondPostTitle}</a>
                </div>
              </div>

              <!-- Similar Post -->
              <div class="col-lg-3 col-md-6 similar_post_col">
                <div class="similar_post trans_200">
                  <a href="blog/{thirdPostSlug}">{thirdPostTitle}</a>
                </div>
              </div>

            </div>
          </div>

          <div class="home_slider_next_container">
            <div
              class="home_slider_next"
              style="background-image:url('{firstPostURL}')">
              <div class="home_slider_next_background trans_400" />
              <div class="home_slider_next_content trans_400">
                <div class="home_slider_next_title">next</div>
                <div class="home_slider_next_link">{firstPostTitle}</div>
              </div>
            </div>
          </div>

        </div>
      </div>

    </div>

    <div class="custom_nav_container home_slider_nav_container">
      <div class="custom_prev custom_prev_home_slider">
        <svg
          version="1.1"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          x="0px"
          y="0px"
          width="7px"
          height="12px"
          viewBox="0 0 7 12"
          enable-background="new 0 0 7 12"
          xml:space="preserve">
          <polyline
            fill="#FFFFFF"
            points="0,5.61 5.609,0 7,0 7,1.438 2.438,6 7,10.563 7,12 5.609,12
            -0.002,6.39 " />
        </svg>
      </div>
      <ul id="custom_dots" class="custom_dots custom_dots_home_slider">
        <li class="custom_dot custom_dot_home_slider active">
          <span />
        </li>
        <li class="custom_dot custom_dot_home_slider">
          <span />
        </li>
        <li class="custom_dot custom_dot_home_slider">
          <span />
        </li>
      </ul>
      <div class="custom_next custom_next_home_slider">
        <svg
          version="1.1"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          x="0px"
          y="0px"
          width="7px"
          height="12px"
          viewBox="0 0 7 12"
          enable-background="new 0 0 7 12"
          xml:space="preserve">
          <polyline
            fill="#FFFFFF"
            points="6.998,6.39 1.389,12 -0.002,12 -0.002,10.562 4.561,6
            -0.002,1.438 -0.002,0 1.389,0 7,5.61 " />
        </svg>
      </div>
    </div>

  </div>
</div>




	<div class="page_content">
		<div class="container">
			<div class="row row-lg-eq-height">

				<!-- Main Content -->

				<div class="col-lg-9">
					<div class="main_content">

						<!-- Blog Section - Don't Miss -->

						<div class="blog_section">
							<div class="section_panel d-flex flex-row align-items-center justify-content-start">
								<div class="section_title">Don't Miss</div>
								<div class="section_tags ml-auto">
									<ul>
										<li class="active"><a href="category.html">all</a></li>
										<li><a href="category.html">style hunter</a></li>
										<li><a href="category.html">vogue</a></li>
										<li><a href="category.html">health & fitness</a></li>
										<li><a href="category.html">travel</a></li>
									</ul>
								</div>
								<div class="section_panel_more">
									<ul>
										<li>more
											<ul>
												<li><a href="category.html">new look 2018</a></li>
												<li><a href="category.html">street fashion</a></li>
												<li><a href="category.html">business</a></li>
												<li><a href="category.html">recipes</a></li>
												<li><a href="category.html">sport</a></li>
												<li><a href="category.html">celebrities</a></li>
											</ul>
										</li>
									</ul>
								</div>
							</div>
							<div class="section_content">
								<div class="grid clearfix">


									<!-- Largest Card With Image -->
                  {#each posts.slice(0,1) as post}
									<div class="card card_largest_with_image grid-item">
										<img class="card-img-top" src="{post.imageBackdrop.url}" alt="https://unsplash.com/@cjtagupa">
										<div class="card-body">
											<div class="card-title"><a href="blog/{post.slug}">{post.title}</a></div>
											<p class="card-text">{post.subtitle}</p>
											<small class="post_meta"><a href="#">{post.author}</a><span>Sep 29, 2017 at 9:48 am</span></small>
										</div>
									</div>
                  {/each}


                  {#each posts.slice(1,3) as post}
									<!-- Small Card Without Image -->
									<div class="card card_default card_small_no_image grid-item">
										<div class="card-body">
											<div class="card-title card-title-small"><a href="blog/{post.slug}">{post.title}</a></div>
											<small class="post_meta"><a href="#">{post.author}</a><span>Sep 29, 2017 at 9:48 am</span></small>
										</div>
									</div>
                  {/each}

                {#each posts.slice(3, 5) as post}
									<!-- Small Card With Image -->
									<div class="card card_small_with_image grid-item">
										<img class="card-img-top" src="{post.imageBackdrop.url}" alt="https://unsplash.com/@jannerboy62">
										<div class="card-body">
											<div class="card-title card-title-small"><a href="blog/{post.slug}">How Did van Gogh’s Turbulent Mind Depict One of the Most Complex Concepts in Physics?</a></div>
											<small class="post_meta"><a href="#">Katy Liu</a><span>Sep 29, 2017 at 9:48 am</span></small>
										</div>
									</div>
                  {/each}

									<!-- Default Card No Image -->
                  {#each posts.slice(5, posts.length + 1) as post}
									<div class="card card_default card_default_no_image grid-item">
										<div class="card-body">
											<div class="card-title card-title-small"><a href="blog/{post.slug}">How Did van Gogh’s Turbulent Mind Depict One of the Most</a></div>
										</div>
									</div>
                  {/each}


								</div>
							</div>
						</div>
</div>
</div>
</div>
</div>
</div>
</div>