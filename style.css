import { pipeline } from 'https://cdn.jsdelivr.net/npm/@xenova/transformers@2.11.0';

let ai;
const chatBox = document.getElementById("chat");
const inputBox = document.getElementById("input");
const loader = document.getElementById("loader");

async function loadAI() {
  showLoader();
  ai = await pipeline('text-generation', 'Xenova/phi-2');
  hideLoader();
  console.log("AI geladen.");
}
loadAI();

async function ask() {
  const input = inputBox.value;
  if (!input.trim()) return;
  chatBox.innerHTML += `<p><strong>Jij:</strong> ${input}</p>`;
  inputBox.value = '';
  showLoader();

  const response = await fetch('faq.txt');
  const faq = await response.text();

  const prompt = `
Je bent een expert in VanMoof fietsen. Gebruik deze informatie om de gebruiker te helpen:

${faq}

Vraag: ${input}
Antwoord:`;

  const out = await ai(prompt, { max_new_tokens: 100 });
  const answer = out[0].generated_text.replace(prompt, '');

  chatBox.innerHTML += `<p><strong>AI:</strong> ${answer}</p>`;
  hideLoader();
}

// Loader functies
function showLoader() {
  loader.classList.remove("hidden");
}
function hideLoader() {
  loader.classList.add("hidden");
}
