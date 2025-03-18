<!DOCTYPE html>
 <html lang="en">
 <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>Custom Slider</title>
 </head>
 <body>
     <script>
         function createSlider(container, min, max, initialValue, type) {
             // Создаём трек (основную линию слайдера)
             const track = document.createElement("div");
             track.style.width = "100%";
             track.style.height = "4px";
 @@ -16,6 +17,7 @@
             track.style.transform = "translateY(-50%)";
             container.appendChild(track);
 
             // Создаём бегунок (thumb)
             const thumb = document.createElement("div");
             thumb.style.width = "20px";
             thumb.style.height = "20px";
 @@ -25,6 +27,7 @@
             thumb.style.cursor = "pointer";
             container.appendChild(thumb);
 
             // Функция изменения цвета при движении
             function updateColor(percent) {
                 if (type === "track") {
                     track.style.background = `linear-gradient(to right, green ${percent * 100}%, pink ${percent * 100}%)`;
 @@ -41,6 +44,7 @@
                 }
             }
 
             // Добавляем деления (divisors) для определённого типа слайдера
             if (type === "divisor") {
                 for (let i = 1; i <= 5; i++) {
                     const divisor = document.createElement("div");
 @@ -53,14 +57,17 @@
                     divisor.style.transform = "translate(-50%, -50%)";
                     container.appendChild(divisor);
                 }
             } else if (type === "thumb") {
             } 
             // Изменяем форму бегунка для типа "thumb"
             else if (type === "thumb") {
                 thumb.style.width = "0";
                 thumb.style.height = "0";
                 thumb.style.borderLeft = "10px solid transparent";
                 thumb.style.borderRight = "10px solid transparent";
                 thumb.style.borderBottom = "15px solid red";
             }
 
             // Логика перетаскивания бегунка
             let dragging = false;
             thumb.addEventListener("mousedown", () => { dragging = true; });
             document.addEventListener("mouseup", () => { dragging = false; });
 @@ -73,11 +80,13 @@
                 updateColor(percent);
             });
 
             // Устанавливаем начальное положение бегунка
             let initialPercent = (initialValue - min) / (max - min);
             thumb.style.left = `${initialPercent * 100}%`;
             updateColor(initialPercent);
         }
 
         // Создаём 4 разных слайдера с разными стилями
         const types = ["track", "divisor", "thumb", "tick"];
         types.forEach((type, index) => {
             const container = document.createElement("div");
