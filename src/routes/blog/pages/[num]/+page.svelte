<script>
	export let data;
	const posts = data.post;
	
	const pages = data.page;
	const pageList = [...Array(Number(pages))].map((_, i) => i + 1);
	console.log(pageList)
	const title = import.meta.env.VITE_TITLE;
</script>

<svelte:head>
	<title>{title}</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>
		{title}
	</h1>

	<div id="post_box">
		{#each posts as post}
			<div class="l-wrapper_01">
				<article class="card_01">
					<div class="card__header_01">
						<p class="card__title_01">{@html post.title.rendered}</p>
						<figure class="card__thumbnail_01">
							<img
								src={post.jetpack_featured_media_url}
								alt="サムネイル"
								class="card__image_01"
								height="320px"
								style="object-fit: cover;height:300px"
							/>
						</figure>
					</div>
					<div class="card__body_01">
						<p class="card__text2_01">
							{@html post.yoast_head_json.og_description.replace(
								/\s+/g,
								""
							)}
						</p>
					</div>
					<div class="card__footer_01">
						<p class="card__text_01">
							<a
								href="/blog/posts/{post.id}"
								class="button_01 -compact"
								>この記事を詳しく見る</a
							>
						</p>
					</div>
				</article>
			</div>
		{/each}
	</div>
	<div id="pagenation">
		{#each pageList as num}
			<span data-sveltekit-reload class="pagenation_num"><a href="/blog/pages/{num}">{num}</a></span>
		{/each}
	</div>
	
</section>

<style>
	h1 {
		width: 100%;
	}

	#post_box {
		display: flex;
		flex-flow: wrap;
	}
	/*--------------------------------------
  カード型_01
--------------------------------------*/
	.l-wrapper_01 {
		margin: 1rem auto;
		width: 465px;
	}

	.l-wrapper_01:hover {
		transform: translateY(-3px);
		box-shadow: 0 7px 14px rgba(50, 50, 93, 0.1),
			0 3px 6px rgba(0, 0, 0, 0.08);
		transition: all 0.5s;
	}

	.card_01 {
		background-color: #fff;
		box-shadow: 0 0 8px rgba(0, 0, 0, 0.16);
		color: #212121;
		text-decoration: none;
	}

	.card__header_01 {
		display: flex;
		flex-wrap: wrap;
	}

	.card__title_01 {
		padding: 1rem 1.5rem 0;
		font-size: 1.6rem;
		order: 1;
		margin-bottom: 0.6rem;
		font-weight: bold;
		text-decoration: none;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 2;
		overflow: hidden;
		height: 50px;
	}

	.card__thumbnail_01 {
		margin: 0;
		order: 0;
		width: 100%;
	}

	.card__image_01 {
		width: 100%;
	}

	.card__body_01 {
		padding: 0 1.5rem;
		height: 100px;
	}

	.card__text_01 {
		font-size: 0.8rem;
		text-align: center;
		text-decoration: none;
		padding-bottom: 0;
	}

	.card__text2_01 {
		font-size: 0.8rem;
		margin-top: 0;
		margin-bottom: 2rem;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 4;
		overflow: hidden;
		height: 65px;
	}

	.card__text_01 + .card__text_01 {
		margin-top: 0.5rem;
	}

	.card__footer_01 {
		padding: 1rem;
		border-top: 1px solid #ddd;
	}

	.button_01 {
		display: inline-block;
		text-decoration: none;
		transition: background-color 0.3s ease-in-out;
		text-align: center;
	}

	.button_01 a {
		text-decoration: none;
	}

	.button_01.-compact {
		padding: 0.5rem 1rem;
		border-radius: 0.25rem;
		background-color: #4f96f6;
		color: #fff;
		font-weight: bold;
		text-decoration: none;
	}

	.button_01.-compact:hover,
	.button_01.-compact:focus {
		background-color: #6bb6ff;
	}

	#pagenation {
		text-align: center;
		display: flex;
  		justify-content: space-evenly;
	}

	.pagenation_num {
	}
</style>
