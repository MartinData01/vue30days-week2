# vue30days-week2

## Vue 30天體驗營，第二週作業

## Vite + Vue

## Vue Composition API

串接 API 登入、註冊及驗證相關狀態

## 註冊

使用者輸入資料，透過 axios post 回傳資料完成註冊，並接收回傳值(Token)

## 登入

使用者輸入資料，透過 axios post 傳送資料並回傳狀態，將回傳值(Token)存在 cookie 中，下次進到頁面自動驗證登入狀態

## 驗證

分為自動及手動
自動：之前有登入過，就會讀取 cookie 自動登入，使用者不需要操作
手動：貼上帳戶的 token 驗證後回傳結果(uid, NickName)
