<script>
  function dropDown(event) {
    let t = event.target.classList;
    if (t.contains("toggle")) {
      t.remove("toggle");
    } else {
      t.add("toggle");
    }
  }

  let p = [
    "ONE Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed \
           do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut \
           enim ad minim veniam, quis nostrud exercitation ullamco laboris \
           nisi ut aliquip ex ea commodo consequat.",
    "TWO Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed \
           do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut \
           enim ad minim veniam, quis nostrud exercitation ullamco laboris \
           nisi ut aliquip ex ea commodo consequat.",
    "THREE Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed \
           do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut \
           enim ad minim veniam, quis nostrud exercitation ullamco laboris \
           nisi ut aliquip ex ea commodo consequat.",
    "FOUR Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed \
           do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut \
           enim ad minim veniam, quis nostrud exercitation ullamco laboris \
           nisi ut aliquip ex ea commodo consequat.",
    "FIVE Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed \
           do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut \
           enim ad minim veniam, quis nostrud exercitation ullamco laboris \
           nisi ut aliquip ex ea commodo consequat.",
    "SIX Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed \
           do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut \
           enim ad minim veniam, quis nostrud exercitation ullamco laboris \
           nisi ut aliquip ex ea commodo consequat."
  ];

  function openNav(event) {
    let x = event.target.value;
    document.getElementById("pinDescription").innerText = p[x];
    document.getElementById("sideNav").style.width = "250px";
    document.getElementById("sideNav").style.display = "block";
  }
  function closeNav(event) {
    document.getElementById("sideNav").style.width = 0;
    document.getElementById("sideNav").style.display = "none";
  }
  // document
  //   .querySelectorAll(".lbl-toggle")
  //   .addEventListener("click", dropDown(event));

  // document
  //   .querySelectorAll(".pinBtn")
  //   .addEventListener("click", openNav(event));
  window.onclick = function(event) {
    if (event.target.className === "pinBtn") {
      openNav(event);
    } else if (event.target.className === "lbl-toggle") {
      dropDown(event);
    } else {
      closeNav(event);
    }
  };
</script>

<style>
  /* global and main style */
  :global(body) {
    margin: 0;
    padding: 0;
  }
  main {
    display: grid;
    grid-template-columns: 1fr 3fr 1fr;
    overflow-y: scroll;
  }
  main > div {
    grid-column: 1 / 1;
  }
  /* underline of section title */
  .pinned-h3:after,
  .secondary-h3:after {
    content: "";
    display: block;
    border-bottom: 1px solid black;
  }
  .pinned-h3 > span,
  .secondary-h3 > span {
    padding-left: 10px;
  }
  /* card styling */
  .pinned div {
    border-radius: 5px;
    height: 200px;
    background-color: #dddddd;
    transition: 0.2s;
    text-align: center;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  }
  /* hover popout for cards */
  .pinned div:hover {
    transform: scale(1.05);
  }
  /* card spacing */
  .pinned {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
    grid-column: 2 / 2;
    padding: 15px 0;
  }
  /* dropdown spacing */
  .secondary {
    display: grid;
    grid-template-columns: 1fr;
    grid-column: 2 / 2;
    padding-bottom: 40px;
  }
  .secondary div {
    background-color: #dddddd;
    transition: 0.2s;
  }
  .collapsible-project {
    border-radius: 7px;
  }
  input[type="checkbox"] {
    display: none;
  }
  .lbl-toggle {
    display: block;

    font-weight: bold;
    font-family: monospace;
    font-size: 1.2rem;
    text-transform: uppercase;

    padding: 1rem;

    color: #1fc8db;
    background: #dddddd;

    cursor: pointer;

    border-radius: 7px;
    transition: all 0.25s ease-out;
  }

  .lbl-toggle:hover {
    color: #2cb5f8;
  }
  .lbl-toggle::before {
    content: " ";
    display: inline-block;

    border-top: 5px solid transparent;
    border-bottom: 5px solid transparent;
    border-left: 5px solid currentColor;

    vertical-align: middle;
    margin-right: 0.7rem;
    transform: translateY(-2px);

    transition: transform 0.2s ease-out;
  }
  .collapsible-content .content-inner {
    background: #03ecfc;
    border-bottom: 1px solid rgba(250, 224, 66, 0.45);

    border-bottom-left-radius: 7px;
    border-bottom-right-radius: 7px;
    padding: 0.5rem 1rem;
  }
  .collapsible-content {
    border-bottom-left-radius: 7px;
    border-bottom-right-radius: 7px;
    max-height: 0px;
    overflow: hidden;

    transition: max-height 0.25s ease-in-out;
  }
  .toggle + .lbl-toggle + .collapsible-content {
    max-height: 100vh;
  }
  .toggle + .lbl-toggle::before {
    transform: rotate(90deg) translateX(-3px);
  }

  .toggle + .lbl-toggle {
    border-bottom-right-radius: 0;
    border-bottom-left-radius: 0;
  }
  #sideNav {
    display: none;
    height: 100%;
    width: 0;
    position: fixed;
    z-index: 1;
    top: 0;
    left: 0;
    background-color: #dddddd;
    overflow-x: hidden;
    padding-top: 60px;
    transition: 0.5s;
    box-shadow: 6px 0 20px 0 rgba(0, 0, 0, 0.19);
  }

  #sideNav .closeBtn {
    position: absolute;
    top: 0;
    right: 25px;
    font-size: 36px;
    margin-left: 50px;
  }

  main {
    transition: margin-left 0.5s;
  }

  @media screen and (max-height: 450px) {
    #sideNav {
      padding-top: 15px;
    }
  }

  #projects {
    grid-column: 1 / 4;
  }
</style>

<div id="sideNav">
  <div>
    <a href="javascript:void(0)" class="closeBtn" on:click={closeNav}>
      &times;
    </a>
    <p id="pinDescription" />
  </div>
</div>

<main id="projects">
  <div>
    <h3 class="pinned-h3">
      <span>Pinned</span>
    </h3>
  </div>
  <section class="pinned">
    <div>
      <h3>Rochambeau</h3>
      <button class="pinBtn" value="0">Read More</button>
    </div>
    <div>
      <h3>Trivia Game</h3>
      <button class="pinBtn" value="1">Read More</button>
    </div>
    <div>
      <h3>Gifaholic</h3>
      <button class="pinBtn" value="2">Read More</button>
    </div>
    <div>
      <h3>Rick Finder</h3>
      <button class="pinBtn" value="3">Read More</button>
    </div>
    <div>
      <h3>Mongo Scraper</h3>
      <button class="pinBtn" value="4">Read More</button>
    </div>
    <div>
      <h3>Word Guess Game</h3>
      <button class="pinBtn" value="5">Read More</button>
    </div>
  </section>
  <div>
    <h3 class="secondary-h3">
      <span>Secondary</span>
    </h3>
  </div>
  <section class="secondary">
    <div class="collapsible-project">
      <input id="collapsible1" type="checkbox" on:click={dropDown} />
      <label for="collapsible1" class="lbl-toggle">Rando 1</label>
      <div class="collapsible-content">
        <div class="content-inner">
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim
            ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
            aliquip ex ea commodo consequat.
          </p>
        </div>
      </div>
    </div>
    <div class="collapsible-project">
      <input id="collapsible2" type="checkbox" on:click={dropDown} />
      <label for="collapsible2" class="lbl-toggle">Rando 2</label>
      <div class="collapsible-content">
        <div class="content-inner">
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim
            ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
            aliquip ex ea commodo consequat.
          </p>
        </div>
      </div>
    </div>
    <div class="collapsible-project">
      <input id="collapsible3" type="checkbox" on:click={dropDown} />
      <label for="collapsible3" class="lbl-toggle">Rando Project</label>
      <div class="collapsible-content">
        <div class="content-inner">
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim
            ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
            aliquip ex ea commodo consequat.
          </p>
        </div>
      </div>
    </div>
    <div class="collapsible-project">
      <input id="collapsible4" type="checkbox" on:click={dropDown} />
      <label for="collapsible4" class="lbl-toggle">Rando Project</label>
      <div class="collapsible-content">
        <div class="content-inner">
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim
            ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
            aliquip ex ea commodo consequat.
          </p>
        </div>
      </div>
    </div>
    <div class="collapsible-project">
      <input id="collapsible5" type="checkbox" on:click={dropDown} />
      <label for="collapsible5" class="lbl-toggle">Rando Project</label>
      <div class="collapsible-content">
        <div class="content-inner">
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim
            ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
            aliquip ex ea commodo consequat.
          </p>
        </div>
      </div>
    </div>
    <div class="collapsible-project">
      <input id="collapsible6" type="checkbox" on:click={dropDown} />
      <label for="collapsible6" class="lbl-toggle">Rando Project</label>
      <div class="collapsible-content">
        <div class="content-inner">
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim
            ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
            aliquip ex ea commodo consequat.
          </p>
        </div>
      </div>
    </div>
  </section>
</main>
