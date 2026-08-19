const card = document.getElementById("loveCard");
const button = document.getElementById("loveButton");
const hiddenMessage = document.getElementById("hiddenMessage");

document.addEventListener("mousemove", (event) => {
  const windowWidth = window.innerWidth;
  const windowHeight = window.innerHeight;

  const mouseX = event.clientX / windowWidth - 0.5;
  const mouseY = event.clientY / windowHeight - 0.5;

  const rotateY = mouseX * 14;
  const rotateX = -mouseY * 14;

  card.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
});

document.addEventListener("mouseleave", () => {
  card.style.transform = "rotateX(0deg) rotateY(0deg)";
});

button.addEventListener("click", () => {
  hiddenMessage.classList.toggle("show");

  if (hiddenMessage.classList.contains("show")) {
    button.textContent = "Guardar este momento";
    createHeartBurst();
  } else {
    button.textContent = "Presiona aquí, Rosa";
  }
});

/* Partículas románticas */
const canvas = document.getElementById("particles");
const ctx = canvas.getContext("2d");

let particles = [];

function resizeCanvas() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
}

window.addEventListener("resize", resizeCanvas);
resizeCanvas();

class HeartParticle {
  constructor(x, y, size, speedY, opacity) {
    this.x = x;
    this.y = y;
    this.size = size;
    this.speedY = speedY;
    this.opacity = opacity;
    this.speedX = Math.random()
