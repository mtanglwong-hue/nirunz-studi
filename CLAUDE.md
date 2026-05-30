# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static single-page portfolio website for **Nirunz_studio**, a Thai freelance web developer. The entire site is a single file: `index.html`. There is no build system, no package manager, and no test framework.

## Development

**No build step required.** Open `index.html` directly in a browser to preview changes.

All external libraries are loaded via CDN — no local installation needed:
- Google Fonts: Prompt + Inter
- Font Awesome 6.5.0 (icons)
- Lightbox2 2.11.4 (portfolio image gallery)
- Formspree (contact form backend, form ID: `mnqwbkgk`)

## File Architecture

Everything lives in `index.html` with this layout:
1. `<head>` — SEO meta, Open Graph, CDN links, and a single inline `<style>` block (~100 lines of CSS)
2. `<body>` — HTML sections in order: header → hero → about → portfolio → services → process → testimonials → pricing → FAQ → contact → footer → back-to-top button
3. Inline `<script>` block at the bottom (scroll-reveal via IntersectionObserver, back-to-top, Lightbox config)
4. `<script type="application/ld+json">` — Organization structured data for SEO

## CSS Conventions

- All styles are in the single `<style>` tag in `<head>` — no external stylesheet
- Responsive breakpoints: **900px** (3-col → 2-col) and **640px** (2-col → 1-col)
- Layout uses CSS Grid with `.grid-3`, `.portfolio-grid`, `.steps`, `.testimonials`, `.pricing` classes
- Fluid typography uses `clamp()` on headings and hero text
- Primary color: `#2563eb` (blue); accent/CTA: `#f59e0b` (amber)

## Scroll-Reveal Animation

All `<section>` elements start hidden (`opacity: 0; transform: translateY(24px)`) and gain the `.visible` class when they enter the viewport (15% threshold). Adding a new section requires no extra JS — the IntersectionObserver picks it up automatically.

## Content Language

Page content is in **Thai** with some English labels (pricing tier names, portfolio tags). Maintain this bilingual pattern when editing: section headings and body copy in Thai, technical/branding terms in English.

## Placeholder Assets

Portfolio images use `https://via.placeholder.com/` URLs. Replace these with real image files or hosted URLs before going to production. The OG image and JSON-LD logo also use placeholder URLs.

## Canonical URL

The canonical URL (`https://nirunz-studio.example/index.html`) and JSON-LD `"url"` field are placeholder values that need to be updated to the actual domain before deployment.

---

## General Rules

* ตอบเป็นภาษาไทยเสมอ
* อธิบายก่อนแก้ไขโค้ดทุกครั้ง
* แก้ไขเฉพาะไฟล์ที่เกี่ยวข้อง
* ห้ามลบฟีเจอร์เดิมโดยไม่ได้รับอนุญาต
* ถ้ามีหลายวิธี ให้เสนอวิธีที่ดีที่สุดก่อน

## UI Design

* ดีไซน์ระดับ SaaS Premium
* Responsive ทุกหน้าจอ (breakpoints: 900px, 640px)
* Mobile First
* ใช้ Animation อย่างพอดี — ปัจจุบันใช้ transition 0.7s บน scroll-reveal
* UI ต้องดูทันสมัยแบบ ChatGPT, Notion, Stripe

## Performance

* ลดการโหลดข้อมูลซ้ำ
* Optimize รูปภาพก่อนใส่ใน portfolio (แทนที่ placeholder URLs)
* คำนึงถึง SEO ทุกหน้า — meta, OG tags, JSON-LD ต้องครบและถูกต้อง

## Security

* Validate Input ทุกจุด (โดยเฉพาะ contact form)
* ป้องกัน XSS ใน JavaScript inline
* ไม่ Hardcode ข้อมูลส่วนตัวหรือ API key ลงใน HTML

## When Creating New Features

1. วิเคราะห์โครงสร้าง `index.html` เดิมก่อน
2. วางแผนว่าจะเพิ่ม section/CSS/JS ตรงไหน
3. แก้ไขไฟล์เดียว (`index.html`) ให้ครบทั้ง HTML, CSS, JS
4. ตรวจสอบว่า scroll-reveal ทำงานถูกต้องกับ section ใหม่
5. สรุปสิ่งที่แก้ไข

## AI Assistant Behavior

* ทำตัวเหมือน Senior Full Stack Developer
* เสนอแนวทางปรับปรุงระบบเสมอ
* ถ้าเจอ Bug ให้หาสาเหตุจริงก่อนแก้
