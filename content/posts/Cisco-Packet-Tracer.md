---
title: Cisco Packet Tracer
date: 2025-04-17T10:20:02+08:00
lastmod: 2025-04-17T10:20:02+08:00
author: Author Name
# avatar: /img/author.jpg
# authorlink: https://author.site
cover: https://hackmd.io/_uploads/BJZ0UyRCyl.png
# images:
#   - /img/cover.jpg
categories:
  - 網路
tags:
  - Network
# nolastmod: true
draft: true
---

網路應用與實務的課程內容，這裡紀錄大部分常用到的指令，並且整理一些比較基本的概念

<!--more-->

## 🔹 層級概念簡介

- `Switch>`：使用者模式 (User EXEC Mode) — 可查看基本資訊。
- `Switch#`：特權模式 (Privileged EXEC Mode) — 可執行設定與查看系統狀態。
- `Switch(config)#`：全域設定模式 (Global Configuration Mode) — 進行系統層級設定。
- `Switch(config-line)#`：行設定模式 (Line Configuration Mode) — 設定 console、VTY 等存取端口。
- `Switch(config-if)#`：介面設定模式 — 設定個別埠的相關參數。

---

### 1. 進入特權模式

```bash
Switch> enable
```
👉 進入特權模式，開始進行系統設定。

---

### 2. 查看目前執行設定

```bash
Switch# show running-config
```
👉 顯示目前記憶體中載入的設定。

---

### 3. 進入全域設定模式

```bash
Switch# configure terminal
```
👉 進入設定模式，準備修改設備參數。

---

### 4. 設定主機名稱

```bash
Switch(config)# hostname S1
```
👉 設定設備名稱為 S1。

---

### 5. 進入 Console 設定模式

```bash
Switch(config)# line console 0
```
👉 進入 console line 設定狀態。

---

### 6. 設定 Console 密碼

```bash
Switch(config-line)# password <密碼>
```
👉 指定 console 密碼為 <密碼>。

---

### 7. 啟用 Console 密碼驗證

```bash
Switch(config-line)# login
```
👉 開啟密碼檢查，使用者登入時需輸入密碼。

---

### 8. 設定 enable 密碼（明碼）

```bash
Switch(config)# enable password <密碼>
```
👉 為特權模式設定明碼密碼。

---

### 9. 設定 enable 密碼（加密）

```bash
Switch(config)# enable secret <密碼>
```
👉 加密版本的 enable 密碼，安全性更高。

---

### 10. 加密所有明碼密碼

```bash
Switch(config)# service password-encryption
```
👉 將所有明碼密碼加密顯示。

---

### 11. 設定 MOTD 警告橫幅

```bash
Switch(config)# banner motd "This is a secure system. Authorized Access Only!"
```
👉 顯示登入警告訊息。

---

### 12. 儲存設定到 NVRAM

```bash
Switch# copy running-config startup-config
```
👉 將目前設定儲存成開機設定。

---

### 13. 查看 NVRAM 設定

```bash
Switch# show startup-config
```
👉 顯示開機時所使用的設定內容。

---

## 📌 附註

- `enable secret` 比 `enable password` 更安全，會自動加密。
- `service password-encryption` 是針對所有未加密密碼啟用加密機制。
- 所有設定都應儲存至 startup-config 以避免開機遺失。