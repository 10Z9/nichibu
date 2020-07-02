<script>
  import { onMount } from "svelte";
  const max = 18;
  const imgstr = 512;

  const imgURL = "https://picsum.photos/600/600/?image=";
  let members = [];

  onMount(() => {
    const list = [];
    for (let i = 0; i < max; i += 1) {
      list.push({
        name: "Giàng A Bưởi",
        image: `${imgURL}${i + imgstr}`,
        quote: "Thế giới có 2 loài, mèo và không phải là mèo",
        intro: `<p>
                  Giàng A Bưởi là sempai siêu nổi tiếng. Tên anh xuất hiện trong tất
                  cả các form của CLB.
                </p>
                <p>
                  Dù nổi tiếng như vậy nhưng thân phận của anh vẫn là một bí mật.
                  Anh được các nichiber gọi với cái tên trìu mến Tiên tri vũ trụ.
                </p>`
      });
    }
    members = list;
  });
</script>

<style>
  .container {
    margin-left: 64px;
  }

  .page {
    width: 1080px;
    margin: 0 auto;
  }

  .page + .page {
    margin-top: 64px;
  }

  .nichibu {
    color: #f24444;
  }

  .intro h1 {
    padding-top: 64px;
    font-weight: bold;
    font-size: 2.1rem;
  }

  .intro h3 {
    max-width: 50%;
    line-height: 1.8rem;
  }

  .core {
    margin: 0 -128px;
    height: 480px;
    display: flex;
  }

  .core .meme {
    background-color: #f2f2f2;
    max-height: 100%;
    border-radius: 6px;
    width: 38%;
    margin-right: 24px;
    overflow: hidden;
    position: relative;
    box-shadow: 0 2px 8px 0 rgba(0, 0, 0, 0.2), 0 3px 20px 0 rgba(0, 0, 0, 0.19);
  }

  .core .mem {
    background-color: #f2f2f2;
    max-height: 100%;
    border-radius: 6px;
    width: 62%;
    overflow: hidden;
    margin-left: 24px;
    box-shadow: 0 2px 8px 0 rgba(0, 0, 0, 0.2), 0 3px 20px 0 rgba(0, 0, 0, 0.19);
  }

  #gallery {
    display: grid;
    height: 100%;
    grid-template: repeat(6, 1fr) / repeat(6, 1fr);
    grid-gap: 4px;
  }

  #gallery > div:nth-child(6n + 1) {
    grid-column: span 2;
    grid-row: span 2;
  }

  #gallery > div:nth-child(2) {
    grid-column: span 3;
    grid-row: span 3;
  }

  #gallery > div:nth-child(4) {
    grid-column: span 1;
    grid-row: span 2;
  }

  #gallery > div > img {
    width: 100%;
    min-height: 100%;
    transition: all ease 0.5s;
  }

  #gallery > div:hover img {
    filter: blur(2px);
    box-shadow: 0 1px 4px 0 rgba(0, 0, 0, 0.2), 0 1px 8px 0 rgba(0, 0, 0, 0.19);
  }

  #gallery > div {
    background-color: rgba(0, 0, 0, 0.12);
    overflow: hidden;
    position: relative;
    cursor: pointer;
  }

  #gallery div {
    display: flex;
    justify-content: center;
    align-items: center;
    text-decoration: none;
  }

  .cover {
    width: 38%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    overflow: hidden;
    background-color: rgba(0, 0, 0, 0.12);
  }

  .cover img {
    height: 100%;
    position: absolute;
    left: 50%;
    transform: translate(-50%, 0);
  }

  .info {
    position: absolute;
    left: 38%;
    top: 0;
    padding: 24px;
    color: rgba(0, 0, 0, 0.8);
  }

  .info > div + div {
    margin-top: 24px;
  }

  .info .header {
    margin-bottom: 16px;
  }

  .name {
    margin-top: 8px;
    font-size: 1.4rem;
  }

  .tags {
    margin-top: 6px;
  }

  .tag {
    display: inline;
    color: rgba(0, 0, 0, 0.55);
  }

  .tag::before {
    content: "#";
    color: rgba(0, 0, 0, 0.45);
  }

  .tag + .tag {
    margin-left: 12px;
  }

  .quote {
    text-align: justify;
    position: relative;
  }

  .quote::before {
    position: absolute;
    font-family: Impact, Haettenschweiler, "Arial Narrow Bold", sans-serif;
    top: -3.5rem;
    left: -0.8rem;
    content: "“";
    font-size: 8rem;
    color: rgba(0, 0, 0, 0.1);
  }

  img.bg {
    height: 100%;
    width: 100%;
    filter: blur(80px);
    position: absolute;
    left: 50%;
    transform: translate(-50%, 0);
  }

  .events {
    display: inline;
  }

  .events > div {
    float: left;
  }

  .events > div + div {
    margin-left: 12px;
  }

  .events .sticker {
    width: 24px;
    height: 24px;
    overflow: hidden;
    border-radius: 100%;
    border: solid 1px #049dd9;
  }

  .events .sticker img {
    height: 100%;
    width: 100%;
  }
</style>

<svelte:head>
  <title>Nichibu</title>
</svelte:head>

<div class="container">
  <section class="page">
    <div class="intro">
      <h1 class="nichibu">HEDSPI Nichibu</h1>
      <h3>
        The quick brown fox jumps over the lazy dog. The quick brown fox jumps
        over the lazy dog. The quick brown fox jumps over the lazy dog
      </h3>
    </div>
  </section>
  <section class="page">
    <div class="core">
      <div class="meme">
        {#if members[1]}
          <img src={members[1].image} alt="avatar" class="bg" />
          <div class="cover">
            <img src={members[1].image} alt="avatar" />
          </div>
          <div class="info">
            <div class="header">
              <div class="name">{members[1].name}</div>
              <div class="tags">
                <div class="tag">k58</div>
                <div class="tag">slave</div>
              </div>
            </div>
            <div class="quote">{members[1].quote}</div>
            <div class="intro">
              {@html members[1].intro}
            </div>
            <div class="events">
              <div>
                <div class="sticker">
                  <img src="/images/2020.jpg" alt="osho2020" />
                </div>
              </div>
              <div>
                <div class="sticker">
                  <img src="/images/2019.jpg" alt="osho2019" />
                </div>
              </div>
            </div>
          </div>
        {/if}
      </div>
      <div class="mem">
        <div id="gallery">
          {#each members as member}
            <div>
              <img src={member.image} alt={member.name} />
            </div>
          {/each}
        </div>
      </div>
    </div>
  </section>
</div>
