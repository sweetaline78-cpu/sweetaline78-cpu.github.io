# sweetaline78-cpu.github.io
theme: jekyll-theme-minimal
title: SweetAline
description: Color and Font Preview
import React, { useState } from "react";

const FONT_OPTIONS = [
  { label: "Roboto", value: "Roboto, sans-serif" },
  { label: "Dancing Script", value: "'Dancing Script', cursive" },
  { label: "Montserrat", value: "'Montserrat', sans-serif" },
  { label: "Indie Flower", value: "'Indie Flower', cursive" },
  { label: "Arial", value: "Arial, sans-serif" },
];

const GOOGLE_FONTS_LINK = `
  <link href="https://fonts.googleapis.com/css?family=Roboto:400,700|Dancing+Script:400,700|Montserrat:400,700|Indie+Flower&display=swap" rel="stylesheet">
`;

// You can inject the Google Fonts link into the document head:
if (typeof document !== "undefined") {
  if (!document.getElementById("google-fonts-preview")) {
    const link = document.createElement("link");
    link.id = "google-fonts-preview";
    link.rel = "stylesheet";
    link.href =
      "https://fonts.googleapis.com/css?family=Roboto:400,700|Dancing+Script:400,700|Montserrat:400,700|Indie+Flower&display=swap";
    document.head.appendChild(link);
  }
}

export default function FontColorPreview() {
  const [text, setText] = useState("Type your custom text here!");
  const [font, setFont] = useState(FONT_OPTIONS[0].value);
  const [color, setColor] = useState("#212121");

  return (
    <div style={{ maxWidth: 500, margin: "2rem auto", padding: "2rem", border: "1px solid #ddd", borderRadius: 8 }}>
      <h2>Font & Color Preview Tool</h2>
      <div style={{ marginBottom: 16 }}>
        <label>
          <strong>Text:</strong>
          <input
            type="text"
            value={text}
            onChange={e => setText(e.target.value)}
            style={{ width: "100%", marginTop: 4, padding: 8, fontSize: 16 }}
          />
        </label>
      </div>
      <div style={{ marginBottom: 16 }}>
        <label>
          <strong>Font:</strong>
          <select
            value={font}
            onChange={e => setFont(e.target.value)}
            style={{ marginLeft: 8, padding: 6, fontSize: 16 }}
          >
            {FONT_OPTIONS.map(opt => (
              <option key={opt.value} value={opt.value}>
                {opt.label}
              </option>
            ))}
          </select>
        </label>
      </div>
      <div style={{ marginBottom: 16 }}>
        <label>
          <strong>Color:</strong>
          <input
            type="color"
            value={color}
            onChange={e => setColor(e.target.value)}
            style={{ marginLeft: 8, width: 36, height: 36 }}
          />
          <span style={{ marginLeft: 8 }}>{color}</span>
        </label>
      </div>
      <div style={{ border: "1px dashed #bbb", minHeight: 80, borderRadius: 6, display: "flex", alignItems: "center", justifyContent: "center", background: "#fafafa" }}>
        <span
          style={{
            fontFamily: font,
            color,
            fontSize: 32,
            transition: "all 0.2s",
            wordBreak: "break-word",
            textAlign: "center",
            width: "100%"
          }}
        >
          {text}
        </span>
      </div>
    </div>
  );
}
