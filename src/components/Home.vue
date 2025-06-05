<template>
  <section id="Home" class="section hero">
    <h2>Hello, I'm <span>Erick</span></h2>
    <p>Aspiring Web Developer</p>
  </section>
</template>

<style scoped>
.hero {
  background: linear-gradient(to right, #00d8ff, #006eff);
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.hero h2 {
  font-size: 2.5em;
  margin-bottom: 0.2em;
}

.hero h2 span {
  color: #ffd700;
}

.hero p {
  font-size: 1.2em;
}
.section {
  padding: 120px 20px;
  min-height: 100vh;
}
</style>
