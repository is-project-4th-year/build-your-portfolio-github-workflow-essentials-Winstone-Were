lucide.createIcons();
const toggle = document.getElementById("menuToggle");
const menu = document.getElementById("menu");

toggle.addEventListener("click", () => {
    menu.classList.toggle("hidden");
});

AOS.init({
    duration: 1000,
    once: true,
    delay: 100,
});
lucide.createIcons();

// Initialize Rellax for all elements with the 'rellax' class
if (window.innerWidth > 768) {
    new Rellax('.rellax', {
        speed: -2,
        center: true,
        round: true,
        vertical: true,
        horizontal: false
    });
}

const squareIDs = ["sq1", "sq2", "sq3", "sq4", "sq5", "sq6", "sq7", "sq8", "sq9", "sq10", "sq11", "sq12", "sq13", "sq14", "sq15", "sq16", "sq17", "sq18", "sq19", "sq20", "sq21", "sq22", "sq23", "sq24"];

squareIDs.forEach((id, index) => {
    anime({
        targets: `#${id}`,
        translateY: [
            { value: -20, duration: 2000 },
            { value: 20, duration: 2000 }
        ],
        easing: "easeInOutSine",
        direction: "alternate",
        loop: true,
        delay: index * 200
    });
});
// Navbar active link logic
const sections = document.querySelectorAll('section');
const navLinks = document.querySelectorAll('.navbar-link');
const nav = document.querySelector('nav'); // Get the navbar element once

window.addEventListener('scroll', () => {
    let current = '';
    const scrollY = window.pageYOffset;

    sections.forEach(section => {
        const sectionTop = section.offsetTop - nav.offsetHeight - 50; // Adjust for navbar height and a small buffer
        const sectionHeight = section.offsetHeight;
        const sectionId = section.getAttribute('id');

        if (scrollY >= sectionTop && scrollY < sectionTop + sectionHeight) {
            current = sectionId;
        }
    });

    navLinks.forEach(link => {
        link.classList.remove('active');
        if (link.getAttribute('href').includes(current)) {
            link.classList.add('active');
        }
    });
});

// Initial check for active link on page load
window.dispatchEvent(new Event('scroll'));