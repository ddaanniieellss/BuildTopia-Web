
// background parallex y on scroll
const background = document.querySelector('.background');
const initialStyles = [...background.children].map((child) => `${getComputedStyle(child).transform}`);
document.addEventListener('scroll', function() {
  const scroll = window.scrollY;
  for (let i = 0; i < background.children.length; i++) {
    const child = background.children[i];
    const style = initialStyles[i];
    const amount = scroll * 0.4;
    child.style = `transform: translateY(${amount}px) ${style}`;
  }
});


function setUpCarousel(carouselContainer) {
  const carousel = carouselContainer.querySelector(".carousel");
  const imagesContainer = carousel.querySelector(".images");
  const images = imagesContainer.querySelectorAll("img");
  const state = { current: 0 };

  const updateStyles = () => {
    const amount = state.current * 100;
    imagesContainer.style.transform = `translate(-${amount}%, 0px)`;
  };

  const onPrev = () => {
    if (state.current > 0) {
      state.current -= 1;
      updateStyles();
    }
  };

  const onNext = () => {
    if (state.current + 1 < images.length) {
      state.current += 1;
      updateStyles();
    }
  };

  imagesContainer.addEventListener("click", () => {
    carouselContainer.classList.add("fullscreen");
  });

  const close = carouselContainer.querySelector(".close");
  close.addEventListener("click", () => {
    carouselContainer.classList.remove("fullscreen");
  });

  const prev = carousel.querySelector(".prev");
  prev.addEventListener("click", onPrev);

  const next = carousel.querySelector(".next");
  next.addEventListener("click", onNext);
}

const carousels = document.querySelectorAll(".carouselContainer");

for (const carousel of carousels) {
  setUpCarousel(carousel);
}

function getRandomInt(max) {
  return Math.floor(Math.random() * max);
}

function createRandomItem() {
  const number = 1 + getRandomInt(232);
  const color = getRandomInt(360);
  const img = document.createElement('img');
  img.src = `assets/items/item-${number}.png`;
  img.width = 64;
  img.height = 80;
  img.style = `image-rendering: pixelated; background-color: hsl(${color}, 53%, 76%)`;
  return img;
}

function moveLeft(items) {
  items.removeChild(items.children[0]);
  items.appendChild(createRandomItem());
  gsap.fromTo(items, { x: 0 }, {
    x: -74,
    duration: 0.8,
    ease: "none",
    onComplete() {
      moveLeft(items);
    }
  });
}

function moveRight(items) {
  items.removeChild(items.children[0]);
  items.appendChild(createRandomItem());
  gsap.fromTo(items, { x: 74 }, {
    x: 148,
    duration: 0.8,
    ease: "none",
    onComplete() {
      moveRight(items);
    }
  });
}

const itemsContainers = document.querySelectorAll(".items");
for (const items of itemsContainers) {
  for (let i = 0; i < 50; i++) {
    items.appendChild(createRandomItem());
  }
}

const leftItemsContainers = document.querySelectorAll(".items.left");
for (const items of leftItemsContainers) {
  moveLeft(items);
}
const rightItemsContainers = document.querySelectorAll(".items.right");
for (const items of rightItemsContainers) {
  moveRight(items);
}

// intro animation
const tl = gsap.timeline();
const logo = document.querySelector(".logo");
const downloadNow = document.querySelector(".downloads h2");
const windows = document.querySelector("#windows");
const linux = document.querySelector("#linux");
tl.fromTo(
  logo,
  {
    y: 150,
  },
  {
    opacity: 1,
    y: 0,
    duration: 2,
  }
);
tl.fromTo(
  downloadNow,
  {
    opacity: 0,
    y: 80,
  },
  {
    opacity: 1,
    y: 0,
    duration: 0.8,
  }
);
tl.fromTo(
  windows,
  {
    opacity: 0,
    y: 50,
  },
  {
    opacity: 1,
    y: 0,
    duration: 0.6,
  }
);
tl.fromTo(
  linux,
  {
    opacity: 0,
    y: 50,
  },
  {
    opacity: 1,
    y: 0,
    duration: 0.6,
  }
);

// scroll animations
const leftContents = document.querySelectorAll(".content.left");
for (const contents of leftContents) {
  const title = contents.querySelector("h1");
  const ps = contents.querySelectorAll("p");
  const tl = gsap.timeline({
    scrollTrigger: title,
  });
  tl.to({}, { duration: 0.5 });
  tl.from(title, {
    opacity: 0,
    x: -100,
    duration: 0.6,
  });
  for (const p of ps) {
    tl.from(p, {
      opacity: 0,
      x: -150,
      duration: 0.9,
    });
  }
}

// scroll animations
const rightContents = document.querySelectorAll(".content.right");
for (const contents of rightContents) {
  const title = contents.querySelector("h1");
  const ps = contents.querySelectorAll("p");
  const tl = gsap.timeline({
    scrollTrigger: title,
  });
  tl.to({}, { duration: 0.5 });
  tl.from(title, {
    opacity: 0,
    x: 100,
    duration: 0.6,
  });
  for (const p of ps) {
    tl.from(p, {
      opacity: 0,
      x: 150,
      duration: 0.9,
    });
  }
}

