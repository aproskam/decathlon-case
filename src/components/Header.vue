<template>
  <header class="page-header vtmn-bg-background-primary">
    <nav class="navbar">
      <button
        type="button"
        class="menu-button"
        aria-controls="main-menu"
        aria-expanded="false"
      >
        <svg aria-hidden="true" class="svg-icon" viewBox="0 0 32 32">
          <path
            d="M3 7h18a1 1 0 010 2H3a1 1 0 110-2zm0 8h22a1 1 0 010 2H3a1 1 0 010-2zm0 8h26a1 1 0 010 2H3a1 1 0 010-2z"
          ></path>
        </svg>
        <span>menu</span>
      </button>
      <div class="logo">
        <a
          href="/"
          tabindex="0"
          aria-label="Sportkleding, sportschoenen en sportartikelen"
        >
          <svg
            role="img"
            aria-label="Decathlon"
            class="decathlon-logo"
            fill="#0082c3"
            viewBox="0 0 176 44"
          >
            <title>Decathlon</title>
            <path
              d="M140.8,22.1c0,3.3-2.7,5.9-5.9,5.9c-3.2,0-5.9-2.6-5.9-5.9c0-3.2,2.7-5.9,5.9-5.9C138.2,16.2,140.8,18.8,140.8,22.1zM20.8,15.9H17v12.4h3.8c1.6,0,3.1-1.1,3.4-2.7c0.4-1.1,0.6-2.3,0.6-3.5c0-1.1-0.2-2.4-0.6-3.4C23.9,17.1,22.4,15.9,20.8,15.9z M67.7,25h3.3l0-4.5L67.7,25L67.7,25z M176,0v44L0,43.9V0H176zM44.2,33.6l0-5.6h-7h0v-3.2h6.3l0-5.6h-6.3v-2.9h7l0-5.7l-13.4,0v7.9c-1.4-4.3-5.4-7.5-10-7.9l-10.2,0v23h10.2c4.5-0.4,8.5-3.6,9.9-7.9v7.9H44.2zM76.8,10.5h-6.5h0l-9.9,14.7c-1,1.6-2.8,2.5-4.7,2.5c-3.1,0-5.6-2.5-5.6-5.6c0-3.1,2.5-5.6,5.6-5.6c0.3,0,0.7-0.1,1-0.1c2.1,0,4.3,0.9,5.8,2.4l2.9-4.5c-2.3-2.4-5.7-3.9-9.1-3.9c-6.3,0-12.1,5.3-12.1,11.6c0,6.3,5.2,11.5,11.5,11.5c3.1,0,6.1-1.3,8.3-3.5h6.8l0,3.5h5.9V10.5zM92.7,10.5l-15,0v5.3h4.6v17.7h5.9v0V15.9h4.6V10.5zM112.3,10.5L112.3,10.5L112.3,10.5L112.3,10.5l-5.9,0l0,8.6h-7l0-8.6h-5.9v23h5.9v-9.1h7v9.1h5.9V10.5zM165.4,10.5h-5.9h0v10.7l-8.1-10.7l-5.4,0l0,8.4c-1.3-4.9-6-8.4-11.1-8.4c-6.3,0-11.5,5.2-11.5,11.5c0,2,0.6,4.1,1.6,5.9h-5.8V10.5h-6v23h13.7v-3.2c2.2,2,5.1,3.2,8.1,3.2c5.2,0,9.7-3.5,11.1-8.4l0,8.4h5.9V22.4l8.1,11.2h5.4L165.4,10.5z"
            ></path>
          </svg>
        </a>
      </div>

      <h1 class="vtmn-typo_display-2 vtmn-px-4">Challenger</h1>
    </nav>
  </header>
</template>

<style>
.page-header {
  position: sticky;
  display: flex;
  flex-direction: column;
  width: 100%;
  top: 0;
  margin-left: 0;
  z-index: 4;
  transform: translate(0);
}

.navbar {
  flex-wrap: nowrap;
  box-shadow: 0 0 0.75rem 0.15rem rgba(26, 42, 52, 0.5);
  display: flex;
  width: 100%;
  align-items: center;
  background-color: #fff;
}

.menu-button {
  align-self: stretch;
  padding-right: 0.5rem;
  padding-left: 0.5rem;
  margin-right: 1.1rem;
  box-shadow: 0.1rem 0 #eff1f3;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-width: 6.6rem;
  text-transform: uppercase;
  font-size: 0.7em;
  text-align: center;
  text-decoration: none;
  outline-offset: -0.2rem;
}

.menu-button svg {
  width: 2.6rem;
  height: 2.6rem;
  margin-bottom: 0.3rem;
}

.logo svg {
  width: 17.6rem;
  height: 4.4rem;
  fill: #007dbc;
  max-width: 100%;
}
</style>
