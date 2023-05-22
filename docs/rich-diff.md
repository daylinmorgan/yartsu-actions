
# Deviation From Rich

## Versions

- Rich: 13.3.5
- Yartsu: 23.5.1b2.dev30+gf5ae41d

## CONSOLE_SVG_FORMAT Diff

```diff
---
+++
@@ -1,5 +1,5 @@
-<svg class="rich-terminal" viewBox="0 0 {width} {height}" xmlns="http://www.w3.org/2000/svg">
-    <!-- Generated with Rich https://www.textualize.io -->
+<svg class="rich-terminal shadow" viewBox="0 0 {width} {height}" xmlns="http://www.w3.org/2000/svg">
+    <!-- Generated with Rich https://www.textualize.io & yartsu https://github.com/daylinmorgan/yartsu -->
     <style>

     @font-face {{
@@ -32,6 +32,10 @@
         font-family: arial;
     }}

+    .shadow {{
+        -webkit-filter: drop-shadow( 2px 5px 2px rgba(0, 0, 0, .7));
+        filter: drop-shadow( 2px 5px 2px rgba(0, 0, 0, .7));
+    }}
     {styles}
     </style>

@@ -43,7 +47,7 @@
     </defs>

     {chrome}
-    <g transform="translate({terminal_x}, {terminal_y})" clip-path="url(#{unique_id}-clip-terminal)">
+    <g transform="translate({terminal_x}, {terminal_y}) scale(.95)" clip-path="url(#{unique_id}-clip-terminal)">
     {backgrounds}
     <g class="{unique_id}-matrix">
     {matrix}

```

## Console.export_svg Diff

```diff
---
+++
@@ -70,9 +70,9 @@
         line_height = char_height * 1.22

         margin_top = 1
-        margin_right = 1
-        margin_bottom = 1
-        margin_left = 1
+        margin_right = char_width * 5 / 6
+        margin_bottom = 20 * 5 / 3
+        margin_left = char_width * 5 / 6

         padding_top = 40
         padding_right = 8
@@ -222,8 +222,8 @@
                 x=terminal_width // 2,
                 y=margin_top + char_height + 6,
             )
-        chrome += f"""
-            <g transform="translate(26,22)">
+        chrome += """
+            <g transform="translate(32,22)">
             <circle cx="0" cy="0" r="7" fill="#ff5f57"/>
             <circle cx="22" cy="0" r="7" fill="#febc2e"/>
             <circle cx="44" cy="0" r="7" fill="#28c840"/>

```

AUTO-GENERATED by scripts/rich-diff