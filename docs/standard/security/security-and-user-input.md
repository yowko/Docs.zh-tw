---
title: "Security and User Input | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "security [.NET Framework], user input"
  - "user input, security"
  - "secure coding, user input"
  - "code security, user input"
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# Security and User Input
使用者資料可以是任何種類的輸入資料 \(來自 Web 要求或 URL 的資料、Microsoft Windows Form 應用程式控制項的輸入內容等\)，由於這種資料通常直接用來當做呼叫其他程式碼的參數，因此會影響到程式碼。  這種情況類似惡意程式碼使用奇怪的參數呼叫您的程式碼，也需採取相同的防範措施。  實際上，使用者輸入的安全比較不易維護，因為這種資料沒有堆疊框架可以追蹤潛在的未受信任資料是否存在。  
  
 這些是最神秘也是最難發現的安全性錯誤；它們可能會存在看起來與安全性完全無關的程式碼中，但是它們卻是將錯誤資料傳遞給其他程式碼的通道。  如果要找出這些錯誤，請注意每一種輸入資料，想像可能的數值範圍，並思考看到這個資料的程式碼是否可以處理所有的狀況。  您可以透過檢查範圍並拒絕程式碼無法處理的任何輸入，以修正這些錯誤。  
  
 與使用者資料相關的部分重要考量事項包括：  
  
-   伺服器回應中的任何使用者資料都會在用戶端的伺服器站台內容中執行。  如果您的 Web 伺服器接受使用者資料並將它插入傳回的網頁中，它可能，例如，含有 **\<script\>** 標記而且會執行，就好像是從伺服器執行一樣。  
  
-   請注意，用戶端可以要求任何 URL。  
  
-   仔細檢查複雜或無效的路徑：  
  
    -   ..\\、非常長的路徑  
  
    -   使用萬用字元 \(\*\)  
  
    -   語彙基元 \(Token\) 展開 \(%token%\)  
  
    -   具有特殊意義的奇怪路徑格式  
  
    -   替代檔案系統資料流名稱，例如 `filename::$DATA`  
  
    -   檔案名稱縮短版，如 `longfilename` 的縮短名稱 `longfi~1`  
  
-   請記住，Eval\(userdata\) 可以執行任何動作。  
  
-   要注意包含某些使用者資料之名稱的晚期繫結。  
  
-   如果您處理的是 Web 資料，請仔細檢查系統允許的各種逸出字元形式，包括：  
  
    -   十六進位逸出字元 \(%nn\)  
  
    -   Unicode 逸出字元 \(%nnn\)  
  
    -   過長的 UTF\-8 逸出字元 \(%nn%nn\)  
  
    -   雙逸出字元 \(%nn 變成 %mmnn，其中的 %mm 是 '%' 的逸出字元\)  
  
-   請留意可能會有多個正式名稱格式的使用者名稱。  例如，在 Microsoft Windows 2000 中，您通常可以使用 MYDOMAIN\\*username* 的格式或 *username*@mydomain.example.com 的格式。  
  
## 請參閱  
 [Secure Coding Guidelines](../../../docs/standard/security/secure-coding-guidelines.md)