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
import { TextLink } from "~/types/links";

enum QuantumHardwarePulsesUrl {
  CalibratingQubitsWithQiskitPulse = "https://learn.qiskit.org/course/quantum-hardware-pulses/calibrating-qubits-using-qiskit-pulse",
  AccessingHigherEnergyStates = "https://learn.qiskit.org/course/quantum-hardware-pulses/accessing-higher-energy-states-with-qiskit-pulse",
  IntroductionToTransmonPhysics = "https://learn.qiskit.org/course/quantum-hardware-pulses/introduction-to-transmon-physics",
  CircuitQuantumElectrodynamics = "https://learn.qiskit.org/course/quantum-hardware-pulses/circuit-quantum-electrodynamics",
  ExploringTheJaynesCummingsHamiltonianWithQiskitPulse = "https://learn.qiskit.org/course/quantum-hardware-pulses/exploring-the-jaynes-cummings-hamiltonian-with-qiskit-pulse",
  MeasuringTheQubitacStakShift = "https://learn.qiskit.org/course/quantum-hardware-pulses/measuring-the-qubit-ac-stark-shift",
  HamiltonianTomography = "https://learn.qiskit.org/course/quantum-hardware-pulses/hamiltonian-tomography",
}

definePageMeta({
  pageTitle: "Investigating Quantum Hardware Using Microwave Pulses",
  routeName: "quantum-hardware-pulses",
});

const config = useRuntimeConfig();

// SEO specific definitions
const title = "Investigating Quantum Hardware Using Microwave Pulses";
const description =
  "These pages explore the physics of superconducting qubits, and using Qiskit to program operations on devices at the level of microwave pulses.";
const image = `${config.public.siteUrl}/images/learn/course/quantum-hardware-pulses/quantum-hardware-pulses.png`;
const pageUrl = `${config.public.siteUrl}/learn/course/quantum-hardware-pulses`;

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

const routeName = "quantum-hardware-pulses";

const headerDescription = [
  "The Qiskit Textbook mostly assumes we have a quantum computer that can carry out quantum operations, and doesn't worry about how the devices actually work. These pages go a step deeper, exploring the physics of superconducting qubits, and using Qiskit to program operations on these devices at the level of microwave pulses.",
];
const headerImg =
  "/images/learn/course/quantum-hardware-pulses/quantum-hardware-pulses.png";

const startLearningCTA: TextLink = {
  url: QuantumHardwarePulsesUrl.CalibratingQubitsWithQiskitPulse,
  label: "Start learning",
  segment: {
    cta: "introduction",
    location: "header",
  },
};

const references: string[] = [];
const externalRecommendedReadingsPreamble = "";
const links: TextLink[] = [];

const courses: Course[] = [
  {
    image: "calibrating-qubits-with-qiskit-pulse.png",
    label: "Calibrating Qubits with Qiskit Pulse",
    segment: {
      cta: "calibrating-qubits-with-qiskit-pulse",
      location: "course",
    },
    url: QuantumHardwarePulsesUrl.CalibratingQubitsWithQiskitPulse,
  },
  {
    image: "accessing-higher-energy-states.png",
    label: "Accessing Higher Energy States",
    segment: { cta: "accessing-higher-energy-states", location: "course" },
    url: QuantumHardwarePulsesUrl.AccessingHigherEnergyStates,
  },
  {
    image: "introduction-to-transmon-physics.png",
    label: "Introduction to Transmon Physics",
    segment: { cta: "introduction-to-transmon-physics", location: "course" },
    url: QuantumHardwarePulsesUrl.IntroductionToTransmonPhysics,
  },
  {
    image: "circuit-quantum-electrodynamics.png",
    label: "Circuit Quantum Electrodynamics",
    segment: { cta: "circuit-quantum-electrodynamics", location: "course" },
    url: QuantumHardwarePulsesUrl.CircuitQuantumElectrodynamics,
  },
  {
    image: "exploring-the-jaynes-cummings-hamiltonian-with-qiskit-pulse.png",
    label: "Exploring the Jaynes-Cummings Hamiltonian with Qiskit Pulse",
    segment: {
      cta: "exploring-the-jaynes-cummings-hamiltonian-with-qiskit-pulse",
      location: "course",
    },
    url: QuantumHardwarePulsesUrl.ExploringTheJaynesCummingsHamiltonianWithQiskitPulse,
  },
  {
    image: "measuring-the-qubit-ac-stak-shift.png",
    label: "Measuring the Qubit ac-Stak Shift",
    segment: { cta: "measuring-the-qubit-ac-stak-shift", location: "course" },
    url: QuantumHardwarePulsesUrl.MeasuringTheQubitacStakShift,
  },
  {
    image: "hamiltonian-tomography.png",
    label: "Hamiltonian Tomography",
    segment: { cta: "hamiltonian-tomography", location: "course" },
    url: QuantumHardwarePulsesUrl.HamiltonianTomography,
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

const imageUrlBase = "/images/learn/course/quantum-hardware-pulses";
</script>
