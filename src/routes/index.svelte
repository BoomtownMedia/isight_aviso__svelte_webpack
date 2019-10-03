<script>
	import { onMount } from "svelte";

  import Header from "../components/Header.svelte";
  let posts = [];
  let tags=['Agriculture', 'Data Analysis', 'Infrastructure', 'Education'];
  let events =[];
  let videos =[];

	$: posts = posts.reverse();
	$: mainPosts = posts.slice(0,1)
	$: otherPosts = posts.slice(1, posts.length)

  let title;
  let firstPostSlug;
  let firstPostTitle;
  let firstPostURL;
  let firstPostCategory;
  let secondPostSlug;
  let secondPostTitle;
  let secondPostURL;
  let secondPostCategory;
  let thirdPostSlug
  let thirdPostTitle;
  let thirdPostURL;
  let thirdPostCategory;

  onMount(async function() {
    const response = await fetch("https://blog-api-isight.herokuapp.com/posts");
    $: posts = await response.json();
    firstPostSlug = posts[0].slug;
    firstPostTitle = posts[0].title;
    firstPostURL = posts[0].imageBackdrop.url;
    firstPostCategory = posts[0].category;
    secondPostSlug = posts[1].slug;
    secondPostTitle = posts[1].title;
    secondPostURL = posts[1].imageBackdrop.url;
    secondPostCategory = posts[1].category;
    thirdPostSlug = posts[2].slug;
    thirdPostTitle = posts[2].title;
    thirdPostURL = posts[2].imageBackdrop.url;
    thirdPostCategory = posts[2].category;

		const res = await fetch("https://blog-api-isight.herokuapp.com/events"); 
    $: events = await res.json();
		const rez = await fetch("https://blog-api-isight.herokuapp.com/videos"); 
    $: videos= await rez.json();
  });


 $: posts.forEach((post)=> {
      tags.push(post.category)
  })
</script>

<style>

</style>

<svelte:head>
  <title>Isight Blog</title>
</svelte:head>
<Header />
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
                    <div class="home_slider_item_category trans_200">
                      <a href="category.html" class="trans_200">
                        {firstPostCategory}
                      </a>
                    </div>
                    <div class="home_slider_item_title">
                      <a href="post.html">{firstPostTitle}</a>
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
                            points="12.475,0 11.061,0 17.081,6.021 0,6.021
                            0,7.021 17.038,7.021 11.06,13 12.474,13 18.974,6.5 " />
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
                    <div class="home_slider_item_category trans_200">
                      <a href="category.html" class="trans_200">
                        {secondPostCategory}
                      </a>
                    </div>
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
                            points="12.475,0 11.061,0 17.081,6.021 0,6.021
                            0,7.021 17.038,7.021 11.06,13 12.474,13 18.974,6.5 " />
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
                    <div class="home_slider_item_category trans_200">
                      <a href="category.html" class="trans_200">
                        {thirdPostCategory}
                      </a>
                    </div>
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
                            points="12.475,0 11.061,0 17.081,6.021 0,6.021
                            0,7.021 17.038,7.021 11.06,13 12.474,13 18.974,6.5 " />
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


						<!-- Blog Section - Latest -->

						<div class="blog_section">
							<div class="section_panel d-flex flex-row align-items-center justify-content-start">
								<div class="section_title">Latest Articles</div>
							</div>
							<div class="section_content">
								<div class="grid clearfix">
									
									<!-- Small Card With Image
									<div class="card card_small_with_image grid-item">
										<img class="card-img-top" src="images/post_10.jpg" alt="">
										<div class="card-body">
											<div class="card-title card-title-small"><a href="post.html">How Did van Gogh’s Turbulent Mind Depict One of the Most Complex Concepts in Physics?</a></div>
											<small class="post_meta"><a href="#">Katy Liu</a><span>Sep 29, 2017 at 9:48 am</span></small>
										</div>
									</div> -->
									<!-- Largest Card with Image-->
									{#each mainPosts as post}
										<div class="card card_largest_with_image grid-item">
										<img class="card-img-top" src="{post.imageBackdrop.url}" alt="https://unsplash.com/@cjtagupa">
										<div class="card-body">
											<div class="card-title"><a href="post.html">{post.title}</a></div>
											<p class="card-text">{post.subtitle}</p>
											<small class="post_meta"><a href="blog/{post.slug}">Katy Liu</a><span>Sep 29, 2017 at 9:48 am</span></small>
										</div>
									</div>
									{/each}
									<!-- Small Card Without Image -->
                  {#each otherPosts as post}
									<div class="card card_default card_small_with_image grid-item">

										<img class="card-img-top" src="{post.imageBackdrop.url}" >
										<div class="card-body">
											<div class="card-title card-title-small"><a href="post.html">{post.title} </a></div>
											<small class="post_meta"><a href="blog/{post.slug}">Katy Liu</a><span>Sep 29, 2017 at 9:48 am</span></small>
										</div>
									</div>
                  {/each}

									<!-- Small Card Without Image -->
									<!-- <div class="card card_default card_small_no_image grid-item">
										<div class="card-body">
											<div class="card-title card-title-small"><a href="post.html">How Did van Gogh’s Turbulent Mind Depict One of the Most Complex Concepts in Physics?</a></div>
											<small class="post_meta"><a href="#">Katy Liu</a><span>Sep 29, 2017 at 9:48 am</span></small>
										</div>
									</div> -->

									<!-- Default Card With Background
									<div class="card card_default card_default_with_background grid-item">
										<div class="card_background" style="background-image:url(images/post_12.jpg)"></div>
										<div class="card-body">
											<div class="card-title card-title-small"><a href="post.html">How Did van Gogh’s Turbulent Mind Depict One of the Most</a></div>
										</div>
									</div>

									<!-- Default Card With Background -->
									<!-- <div class="card card_default card_default_with_background grid-item">
										<div class="card_background" style="background-image:url(images/post_6.jpg)"></div>
										<div class="card-body">
											<div class="card-title card-title-small"><a href="post.html">How Did van Gogh’s Turbulent Mind Depict One of the Most</a></div>
										</div>
									</div> --> 
								</div>
								
							</div>
						</div>

					</div>
					<div class="load_more">
						<div id="load_more" class="load_more_button text-center trans_200">Load More</div>
					</div>
				</div>

				<!-- Sidebar -->

				<div class="col-lg-3">
					<div class="sidebar">
						<div class="sidebar_background"></div>

<!-- Top Stories -->

						<div class="sidebar_section">
							<div class="sidebar_title_container">
								<div class="sidebar_title">Top Stories</div>
								<div class="sidebar_slider_nav">
									<div class="custom_nav_container sidebar_slider_nav_container">
										<div class="custom_prev custom_prev_top">
											<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
												 width="7px" height="12px" viewBox="0 0 7 12" enable-background="new 0 0 7 12" xml:space="preserve">
												<polyline fill="#bebebe" points="0,5.61 5.609,0 7,0 7,1.438 2.438,6 7,10.563 7,12 5.609,12 -0.002,6.39 "/>
											</svg>
										</div>
								        <ul id="custom_dots" class="custom_dots custom_dots_top">
											<li class="custom_dot custom_dot_top active"><span></span></li>
											<li class="custom_dot custom_dot_top"><span></span></li>
											<li class="custom_dot custom_dot_top"><span></span></li>
										</ul>
										<div class="custom_next custom_next_top">
											<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
												 width="7px" height="12px" viewBox="0 0 7 12" enable-background="new 0 0 7 12" xml:space="preserve">
												<polyline fill="#bebebe" points="6.998,6.39 1.389,12 -0.002,12 -0.002,10.562 4.561,6 -0.002,1.438 -0.002,0 1.389,0 7,5.61 "/>
											</svg>
										</div>
									</div>
								</div>
							</div>
							<div class="sidebar_section_content">

								<!-- Top Stories Slider -->
								<div class="sidebar_slider_container">
									<div class="owl-carousel owl-theme sidebar_slider_top">

										<!-- Top Stories Slider Item -->
										<div class="owl-item">

											<!-- Sidebar Post -->
											{#each posts as post}
											<div class="side_post">
												<a href="blog/{post.slug}.html">
													<div class="d-flex flex-row align-items-xl-center align-items-start justify-content-start">
														<div class="side_post_image"><div><img src="{post.imageBackdrop.url}" alt=""></div></div>
														<div class="side_post_content">
															<div class="side_post_title">{post.title}</div>
															<small class="post_meta">{post.author}<span> {new Date(post.createdAt).toLocaleDateString('default')}</span></small>
														</div>
													</div>
												</a>
											</div>
											{/each}
										</div>
									</div>
								</div>
						</div>
						</div>

						<!-- Newest Videos -->

						<div class="sidebar_section newest_videos">
							<div class="sidebar_title_container">
								<div class="sidebar_title">Newest Videos</div>
								<div class="sidebar_slider_nav">
									<div class="custom_nav_container sidebar_slider_nav_container">
										<div class="custom_prev custom_prev_vid">
											<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
												 width="7px" height="12px" viewBox="0 0 7 12" enable-background="new 0 0 7 12" xml:space="preserve">
												<polyline fill="#bebebe" points="0,5.61 5.609,0 7,0 7,1.438 2.438,6 7,10.563 7,12 5.609,12 -0.002,6.39 "/>
											</svg>
										</div>
								        <ul id="custom_dots" class="custom_dots custom_dots_vid">
											<li class="custom_dot custom_dot_vid active"><span></span></li>
											<li class="custom_dot custom_dot_vid"><span></span></li>
											<li class="custom_dot custom_dot_vid"><span></span></li>
										</ul>
										<div class="custom_next custom_next_vid">
											<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
												 width="7px" height="12px" viewBox="0 0 7 12" enable-background="new 0 0 7 12" xml:space="preserve">
												<polyline fill="#bebebe" points="6.998,6.39 1.389,12 -0.002,12 -0.002,10.562 4.561,6 -0.002,1.438 -0.002,0 1.389,0 7,5.61 "/>
											</svg>
										</div>
									</div>
								</div>
							</div>
							<div class="sidebar_section_content">

								<!-- Sidebar Slider -->
								<div class="sidebar_slider_container">
									<div class="owl-carousel owl-theme sidebar_slider_vid">

										<!-- Newest Videos Slider Item -->
										<div class="owl-item">
                      {#each videos as video}
											<!-- Newest Videos Post -->
											<div class="side_post">
												<a href={video.url}>
													<div class="d-flex flex-row align-items-xl-center align-items-start justify-content-start">
														<div class="side_post_image"><div><img src="images/vid_1.jpg" alt=""></div></div>
														<div class="side_post_content">
															<div class="side_post_title">{video.title}</div>
														</div>
													</div>
												</a>
											</div>

                      {/each}

										</div>

										<!-- Newest Videos Slider Item -->
										<div class="owl-item">

											<!-- Newest Videos Post -->
											<div class="side_post">
												<a href="post.html">
													<div class="d-flex flex-row align-items-xl-center align-items-start justify-content-start">
														<div class="side_post_image"><div><img src="images/vid_1.jpg" alt=""></div></div>
														<div class="side_post_content">
															<div class="side_post_title">How Did van Gogh’s Turbulent Mind</div>
															<small class="post_meta">Katy Liu<span>Sep 29</span></small>
														</div>
													</div>
												</a>
											</div>

											<!-- Newest Videos Post -->
											<div class="side_post">
												<a href="post.html">
													<div class="d-flex flex-row align-items-xl-center align-items-start justify-content-start">
														<div class="side_post_image"><div><img src="images/vid_2.jpg" alt=""></div></div>
														<div class="side_post_content">
															<div class="side_post_title">How Did van Gogh’s Turbulent Mind</div>
															<small class="post_meta">Katy Liu<span>Sep 29</span></small>
														</div>
													</div>
												</a>
											</div>

											<!-- Newest Videos Post -->
											<div class="side_post">
												<a href="post.html">
													<div class="d-flex flex-row align-items-xl-center align-items-start justify-content-start">
														<div class="side_post_image"><div><img src="images/vid_3.jpg" alt=""></div></div>
														<div class="side_post_content">
															<div class="side_post_title">How Did van Gogh’s Turbulent Mind</div>
															<small class="post_meta">Katy Liu<span>Sep 29</span></small>
														</div>
													</div>
												</a>
											</div>

											<!-- Newest Videos Post -->
											<div class="side_post">
												<a href="post.html">
													<div class="d-flex flex-row align-items-xl-center align-items-start justify-content-start">
														<div class="side_post_image"><div><img src="images/vid_4.jpg" alt=""></div></div>
														<div class="side_post_content">
															<div class="side_post_title">How Did van Gogh’s Turbulent Mind</div>
															<small class="post_meta">Katy Liu<span>Sep 29</span></small>
														</div>
													</div>
												</a>
											</div>

										</div>

										<!-- Newest Videos Slider Item -->
										<div class="owl-item">

											<!-- Newest Videos Post -->
											<div class="side_post">
												<a href="post.html">
													<div class="d-flex flex-row align-items-xl-center align-items-start justify-content-start">
														<div class="side_post_image"><div><img src="images/vid_1.jpg" alt=""></div></div>
														<div class="side_post_content">
															<div class="side_post_title">How Did van Gogh’s Turbulent Mind</div>
															<small class="post_meta">Katy Liu<span>Sep 29</span></small>
														</div>
													</div>
												</a>
											</div>

											<!-- Newest Videos Post -->
											<div class="side_post">
												<a href="post.html">
													<div class="d-flex flex-row align-items-xl-center align-items-start justify-content-start">
														<div class="side_post_image"><div><img src="images/vid_2.jpg" alt=""></div></div>
														<div class="side_post_content">
															<div class="side_post_title">How Did van Gogh’s Turbulent Mind</div>
															<small class="post_meta">Katy Liu<span>Sep 29</span></small>
														</div>
													</div>
												</a>
											</div>

											<!-- Newest Videos Post -->
											<div class="side_post">
												<a href="post.html">
													<div class="d-flex flex-row align-items-xl-center align-items-start justify-content-start">
														<div class="side_post_image"><div><img src="images/vid_3.jpg" alt=""></div></div>
														<div class="side_post_content">
															<div class="side_post_title">How Did van Gogh’s Turbulent Mind</div>
															<small class="post_meta">Katy Liu<span>Sep 29</span></small>
														</div>
													</div>
												</a>
											</div>

											<!-- Newest Videos Post -->
											<div class="side_post">
												<a href="post.html">
													<div class="d-flex flex-row align-items-xl-center align-items-start justify-content-start">
														<div class="side_post_image"><div><img src="images/vid_4.jpg" alt=""></div></div>
														<div class="side_post_content">
															<div class="side_post_title">How Did van Gogh’s Turbulent Mind</div>
															<small class="post_meta">Katy Liu<span>Sep 29</span></small>
														</div>
													</div>
												</a>
											</div>

										</div>

									</div>
								</div>
							</div>
						</div>

				
						<!-- Future Events -->

						<div class="sidebar_section future_events">
							<div class="sidebar_title_container">
								<div class="sidebar_title">Future Events</div>
								<div class="sidebar_slider_nav">
									<div class="custom_nav_container sidebar_slider_nav_container">
										<div class="custom_prev custom_prev_events">
											<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
												 width="7px" height="12px" viewBox="0 0 7 12" enable-background="new 0 0 7 12" xml:space="preserve">
												<polyline fill="#bebebe" points="0,5.61 5.609,0 7,0 7,1.438 2.438,6 7,10.563 7,12 5.609,12 -0.002,6.39 "/>
											</svg>
										</div>
								        <ul id="custom_dots" class="custom_dots custom_dots_events">
											<li class="custom_dot custom_dot_events active"><span></span></li>
											<li class="custom_dot custom_dot_events"><span></span></li>
											<li class="custom_dot custom_dot_events"><span></span></li>
										</ul>
										<div class="custom_next custom_next_events">
											<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
												 width="7px" height="12px" viewBox="0 0 7 12" enable-background="new 0 0 7 12" xml:space="preserve">
												<polyline fill="#bebebe" points="6.998,6.39 1.389,12 -0.002,12 -0.002,10.562 4.561,6 -0.002,1.438 -0.002,0 1.389,0 7,5.61 "/>
											</svg>
										</div>
									</div>
								</div>
							</div>
							<div class="sidebar_section_content">

								<!-- Sidebar Slider -->
								<div class="sidebar_slider_container">
									<div class="owl-carousel owl-theme sidebar_slider_events">

										<!-- Future Events Slider Item -->
										<div class="owl-item">

											<!-- Future Events Post -->
											{#each events as event}
											<div class="side_post">
												<a href="post.html">
													<div class="d-flex flex-row align-items-xl-center align-items-start justify-content-start">
														<div class="event_date d-flex flex-column align-items-center justify-content-center">
															<div class="event_day">{new Date(event.event_date).toLocaleDateString('default', { day: 'numeric'})}</div>
															<div class="event_month">{new Date(event.event_date).toLocaleDateString('default', { month: 'short'})}</div>
														</div>
														<div class="side_post_content">
															<div class="side_post_title">{event.title}</div>
															<small class="post_meta">{event.author}<span>{new Date(event.createdAt).toLocaleDateString('default')}</span></small>
														</div>
													</div>
												</a>
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
	</div>