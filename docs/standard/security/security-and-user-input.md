---
title: 安全性和使用者輸入
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
caps.latest.revision: ''
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 157e20a80f0a76e157fad091bec6bfe635a9ccb8
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="security-and-user-input"></a>安全性和使用者輸入
使用者資料，也就是任何種類的輸入 (來自 Web 要求或 URL 的資料、對 Microsoft Windows Forms 應用程式之控制項的輸入等等)，可以會對程式碼有不良影響，因為通常該資料會直接做為參數來呼叫其他程式碼。 這種情況類似惡意程式碼使用奇怪的參數呼叫您的程式碼，應該採取相同的預防措施。 使用者輸入實際上較難以保護其安全，因為沒有任何堆疊框架，可以追蹤可能不受信任的資料存在。  
  
 它們是在最細微且最難以尋找的安全性錯誤當中，因為，雖然它們可以存在於似乎是與安全性沒有相關的程式碼中，但是它們是將錯誤資料傳遞給其他程式碼的閘道。 若要找出這些錯誤，請依照下列任何一種輸入資料，想像一下可能值的範圍，並且考量查看此資料的程式碼是否可以處理所有這些情況。 您可以透過檢查範圍以及拒絕程式碼無法處理的任何輸入，來修正這些錯誤。  
  
 與使用者資料相關的一些重要考量包括下列項目︰  
  
-   伺服器回應的任何使用者資料會在用戶端的伺服器網站內容中執行。 例如，如果您的 Web 伺服器接受使用者資料並將它插入傳回的網頁中，它可能會包含 **\<script>** 標記，並且看起來就像是從伺服器執行。  
  
-   請記住，用戶端可以要求任何 URL。  
  
-   請考慮棘手或無效的路徑︰  
  
    -   ..\，非常長的路徑。  
  
    -   使用萬用字元 (*)。  
  
    -   語彙基元展開 (%token%)。  
  
    -   具有特殊意義的奇怪格式路徑。  
  
    -   替代的檔案系統資料流名稱，例如 `filename::$DATA`。  
  
    -   簡短版本的檔案名稱，例如 `longfilename` 的 `longfi~1`。  
  
-   請記住，Eval(userdata) 可以執行任何動作。  
  
-   請小心晚期繫結至包含一些使用者資料的名稱。  
  
-   如果您正在處理 Web 資料，請考慮允許的各種形式逸出，包括︰  
  
    -   十六進位逸出 (%nn)。  
  
    -   Unicode 逸出 (%nnn)。  
  
    -   過長 UTF-8 逸出 (%nn%nn)。  
  
    -   雙逸出 (%nn 變成 %mmnn，其中 %mm 是 '%' 的逸出)。  
  
-   請小心可能有一個以上標準格式的使用者名稱。 例如，您通常可以使用 MYDOMAIN\\username 形式或 username@mydomain.example.com 形式。  
  
## <a name="see-also"></a>另請參閱  
 [安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)
