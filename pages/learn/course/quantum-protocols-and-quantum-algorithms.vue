<template>
  <LearnCourse
    :courses="courses"
    :external-recommended-readings-preamble="
      externalRecommendedReadingsPreamble
    "
    :header-title="title"
    :header-description="headerDescription"
    :header-img="headerImg"
    :image-url-base="imageUrlBase"
    :links="links"
    :prerequisites="prerequisites"
    :references="references"
    :route-name="routeName"
    :start-learning-cta="startLearningCTA"
  />
</template>

<script setup lang="ts">
import { Course, Prerequisite } from "constants/learnContent";
import { RecommendedReading } from "~/types/learn";
import { TextLink } from "~/types/links";

enum QuantumProtocolsAndQuantumAlgorithmsUrl {
  DefiningQuantumCircuits = "https://learn.qiskit.org/course/ch-algorithms/quantum-circuits",
  DeutschJozsaAlgorithm = "https://learn.qiskit.org/course/ch-algorithms/deutsch-jozsa-algorithm",
  BernsteinVaziraniAlgorithm = "https://learn.qiskit.org/course/ch-algorithms/bernstein-vazirani-algorithm",
  SimonsAlgorithm = "https://learn.qiskit.org/course/ch-algorithms/simons-algorithm",
  QuantumFourierTransformation = "https://learn.qiskit.org/course/ch-algorithms/quantum-fourier-transform",
  QuantumPhaseEstimation = "https://learn.qiskit.org/course/ch-algorithms/quantum-phase-estimation",
  ShorsAlgorithm = "https://learn.qiskit.org/course/ch-algorithms/shors-algorithm",
  GroversAlgorithm = "https://learn.qiskit.org/course/ch-algorithms/grovers-algorithm",
  QuantumCounting = "https://learn.qiskit.org/course/ch-algorithms/quantum-counting",
  QuantumTeleportation = "https://learn.qiskit.org/course/ch-algorithms/quantum-teleportation",
  SuperdenseCoding = "https://learn.qiskit.org/course/ch-algorithms/superdense-coding",
  QuantumKeyDistribution = "https://learn.qiskit.org/course/ch-algorithms/quantum-key-distribution",
  QuantumWalkSearchAlgorithm = "https://learn.qiskit.org/course/ch-algorithms/quantum-walk-search-algorithm",
  HiddenShiftProblem = "https://learn.qiskit.org/course/ch-algorithms/hidden-shift-problem",
}

definePageMeta({
  pageTitle: "Quantum Protocols and Quantum Algorithms",
  routeName: "quantum-protocols-and-quantum-algorithms",
});

const config = useRuntimeConfig();

// SEO specific definitions
const title = "Quantum Protocols and Quantum Algorithms";
const description =
  "Discover quantum gates, operations, and algorithms that surpass classical counterparts. Explore their properties and practical applications.";
const image = `${config.public.siteUrl}/images/learn/course/quantum-protocols-and-quantum-algorithms/quantum-protocols-and-quantum-algorithms.png`;
const pageUrl = `${config.public.siteUrl}/learn/course/quantum-protocols-and-quantum-algorithms`;

useSeoMeta({
  title,
  ogTitle: title,
  description,
  ogDescription: description,
  ogImage: image,
  ogImageAlt: title,
  ogUrl: pageUrl,
  ogType: "website",
  twitterCard: "summary_large_image",
  twitterDescription: description,
});

const routeName = "quantum-protocols-and-quantum-algorithms";

const headerDescription = [
  "So far, we've seen various quantum gates and operations, and we've explored some interesting properties of these gates. Each of these pages shows how we can combine quantum operations into a quantum algorithm that outperforms their classical counterpart. As a bonus, some of these algorithms are actually useful too!",
];
const headerImg =
  "/images/learn/course/quantum-protocols-and-quantum-algorithms/quantum-protocols-and-quantum-algorithms.png";

const startLearningCTA: TextLink = {
  url: QuantumProtocolsAndQuantumAlgorithmsUrl.DefiningQuantumCircuits,
  label: "Start learning",
  segment: {
    cta: "introduction",
    location: "header",
  },
};

const references: string[] = [];
const externalRecommendedReadingsPreamble = "";
const links: RecommendedReading[] = [
  {
    url: "https://www.cambridge.org/highereducation/books/quantum-computation-and-quantum-information/01E10196D0A682A6AEFFEA52D53BE9AE#overview",
    author: "Michael Nielsen, et al.,",
    label: "Quantum Computation and Quantum Information (Chapters 4-6)",
    segment: {
      cta: "quantum-computation-and-quantum-information",
      location: "external-recommended-readings",
    },
  },
  {
    url: "https://global.oup.com/academic/product/an-introduction-to-quantum-computing-9780198570493?cc=nl&lang=en&",
    author: "Phillip Kaye, et al.,",
    label: "An Introduction to Quantum Computing (Chapters 5-8)",
    segment: {
      cta: "an-introduction-to-quantum-computing",
      location: "external-recommended-readings",
    },
  },
  {
    url: "http://cleve.iqc.uwaterloo.ca/resources/QIC-710-F21/Qic710QuantumAlgorithmsPart1.pdf",
    author: "Richard Cleve,",
    label: "Quantum Information Processing — Quantum Algorithms I",
    segment: {
      cta: "quantum-information-processing",
      location: "external-recommended-readings",
    },
  },
  {
    url: "http://cleve.iqc.uwaterloo.ca/resources/QIC-710-F21/Qic710QuantumAlgorithmsPart2.pdf",
    author: "Richard Cleve,",
    label: "Quantum Information Processing — Quantum Algorithms II",
    segment: {
      cta: "quantum-information-processing",
      location: "external-recommended-readings",
    },
  },
  {
    url: "http://cleve.iqc.uwaterloo.ca/resources/QIC-710-F21/Qic710QuantumAlgorithmsPart3.pdf",
    author: "Richard Cleve,",
    label: "Quantum Information Processing — Quantum Algorithms III",
    segment: {
      cta: "quantum-information-processing",
      location: "external-recommended-readings",
    },
  },
];

const courses: Course[] = [
  {
    image: "defining-quantum-circuits.png",
    label: "Defining Quantum Circuits",
    segment: { cta: "defining-quantum-circuits", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.DefiningQuantumCircuits,
  },
  {
    image: "deutsch-jozsa-algorithm.png",
    label: "Deutsch-Jozsa Algorithm",
    segment: { cta: "deutsch-jozsa-algorithm", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.DeutschJozsaAlgorithm,
  },
  {
    image: "bernstein-vazirani-algorithm.png",
    label: "Bernstein-Vazirani Algorithm",
    segment: { cta: "bernstein-vazirani-algorithm", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.BernsteinVaziraniAlgorithm,
  },
  {
    image: "simons-algorithm.png",
    label: "Simon’s Algorithm",
    segment: { cta: "simons-algorithm", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.SimonsAlgorithm,
  },
  {
    image: "quantum-fourier-transformation.png",
    label: "Quantum Fourier Transformation",
    segment: { cta: "quantum-fourier-transformation", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.QuantumFourierTransformation,
  },
  {
    image: "quantum-phase-estimation.png",
    label: "Quantum Phase Estimation",
    segment: { cta: "quantum-phase-estimation", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.QuantumPhaseEstimation,
  },
  {
    image: "shors-algorithm.png",
    label: "Shor’s Algorithm",
    segment: { cta: "shors-algorithm", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.ShorsAlgorithm,
  },
  {
    image: "grovers-algorithm.png",
    label: "Grover’s Algorithm",
    segment: { cta: "grovers-algorithm", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.GroversAlgorithm,
  },
  {
    image: "quantum-counting.png",
    label: "Quantum Counting",
    segment: { cta: "quantum-counting", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.QuantumCounting,
  },
  {
    image: "quantum-walk-search.png",
    label: "Quantum Walk Search Algorithm",
    segment: { cta: "quantum-walk-search-algorithm", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.QuantumWalkSearchAlgorithm,
  },
  {
    image: "hidden-shift-problem.png",
    label: "Hidden Shift Problem",
    segment: { cta: "hidden-shift-problem", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.HiddenShiftProblem,
  },
  {
    image: "quantum-key-distribution.png",
    label: "Quantum Key Distribution",
    segment: { cta: "quantum-key-distribution", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.QuantumKeyDistribution,
  },
  {
    image: "superdense-coding.png",
    label: "Superdense Coding",
    segment: { cta: "superdense-coding", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.SuperdenseCoding,
  },
  {
    image: "quantum-teleportation.png",
    label: "Quantum Teleportation",
    segment: { cta: "quantum-teleportation", location: "course" },
    url: QuantumProtocolsAndQuantumAlgorithmsUrl.QuantumTeleportation,
  },
];

const prerequisites: Prerequisite[] = [
  {
    title: "Multiple Qubits and Entanglement",
    description:
      "With the basics down, this chapter explores the consequences of these new quantum effects, and sets us up with tools to understand quantum algorithms.",
    segment: {
      cta: "multiple-qubits-and-entanglement",
      location: "prerequisite-material",
    },
    url: "https://learn.qiskit.org/course/ch-gates/introduction",
  },
  {
    title: "Python and Jupyter Notebooks",
    description:
      "Python is a programming language where you don't need to compile. You can just run it line by line...",
    segment: {
      cta: "python-and-jupyter-notebooks",
      location: "prerequisite-material",
    },
    url: "https://learn.qiskit.org/course/ch-prerequisites/introduction-to-python-and-jupyter-notebooks",
  },
];

const imageUrlBase =
  "/images/learn/course/quantum-protocols-and-quantum-algorithms";
</script>
