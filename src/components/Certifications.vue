<template>
    <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:px-8">
        <h2 class="text-4xl font-semibold text-gray-900 text-center mb-12">Certifications</h2>

        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
            <div v-for="(cert, index) in certs" :key="index" :class="[
                'transition-all duration-500 rounded-lg overflow-hidden p-6',
                getCardBackgroundColor(index),
                getCardAnimation(index)
            ]" class="card">
                <!-- Certification Image -->
                <img v-if="cert.image" :src="cert.image" alt="Certification Image"
                    class="w-full h-48 object-cover rounded-lg mb-6" />

                <!-- Certification Title -->
                <h3
                    class="text-2xl font-semibold text-gray-800 hover:text-primary transition duration-300 cursor-pointer">
                    {{ cert.title }}
                </h3>

                <!-- Institution Name -->
                <p class="text-gray-600 mt-2">{{ cert.description }}</p>

                <!-- Date -->
                <p class="text-gray-500 text-sm mt-1">{{ cert.date }}</p>

                <!-- Certificate Link -->
                <div class="mt-4">
                    <a v-if="cert.link" :href="cert.link" target="_blank"
                        class="text-primary font-semibold hover:text-yellow-500 transition duration-300">
                        View Certificate
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { inject } from "vue";

// Inject the certifications data provided by the parent component
const certs = inject("certs");

// Dynamic background colors for cards based on the index
const colors = [
    "bg-indigo-100", // Light Indigo
    "bg-teal-100", // Light Teal
    "bg-green-100", // Light Green
    "bg-purple-100", // Light Purple
    "bg-pink-100", // Light Pink
    "bg-blue-100", // Light Blue
];

// Return different background colors based on index
const getCardBackgroundColor = (index) => {
    return colors[index % colors.length];
};

// Different animation effects based on index
const animations = [
    "transition-transform transform hover:scale-105 hover:shadow-xl",
    "transition-transform transform hover:rotate-3 hover:shadow-lg",
    "transition-transform transform hover:scale-110 hover:shadow-xl",
    "transition-transform transform hover:scale-105 hover:translate-y-3 hover:shadow-2xl",
    "transition-transform transform hover:rotate-6 hover:shadow-xl",
    "transition-transform transform hover:scale-120 hover:shadow-lg",
];

// Return different animations based on index
const getCardAnimation = (index) => {
    return animations[index % animations.length];
};
</script>

<style scoped>
/* Primary color for hover effects and links */
:root {
    --primary: #1abc9c;
    /* You can change the primary color here */
}

/* Card Styling */
.card {
    background-color: #fff;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    transition: transform 0.5s ease, box-shadow 0.5s ease;
}

/* Hover effect: Card expands and shadow deepens */
.card:hover {
    transform: translateY(-8px);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

/* Image Styling */
.card img {
    object-fit: cover;
    height: 200px;
    width: 100%;
    border-radius: 8px;
    transition: transform 0.5s ease;
}

.card:hover img {
    transform: scale(1.05);
}

/* Title Styling */
.card h3 {
    font-size: 1.25rem;
    font-weight: 600;
    color: #333;
    margin-top: 16px;
    transition: color 0.3s ease;
}

/* Hover effect on title */
.card h3:hover {
    color: var(--primary);
}

/* Institution Name Styling */
.card p:nth-of-type(2) {
    font-size: 1rem;
    color: #777;
    margin-top: 8px;
}

/* Date Styling */
.card p:nth-of-type(3) {
    font-size: 0.875rem;
    color: #aaa;
    margin-top: 4px;
}

/* Link Button Styling */
.card a {
    margin-top: 16px;
    font-weight: 600;
    color: var(--primary);
    transition: color 0.3s ease;
}

/* Hover effect on link */
.card a:hover {
    color: #f39c12;
}
</style>