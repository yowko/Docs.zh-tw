---
title: "對等名稱和 PNRP 識別碼 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
caps.latest.revision: 5
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 5
---
# 對等名稱和 PNRP 識別碼
對等名稱表示通訊的端點，可以是電腦、使用者、群組，服務或任何與對等電腦可以解析為 IPv6 位址。  對等名稱解析通訊協定 \(PNRP\) 以統計資料為唯一的對等名稱 PNRP ID 的建立，用來識別 Cloud 成員。  
  
## 對等名稱  
 對等名稱可以登錄為不安全或取得。  不安全的名稱是受到欺騙的文字字串，，因為任何人都可以註冊一個複製不安全的名稱。  不安全的名稱最適合用於私用或保護的網路。  取得名稱保護憑證和數位簽章。  只有原始的發行者可以識別受保護的名稱的擁有權。  
  
 Cloud 和範圍的組合會參與 PNRP 活動的對等電腦提供合理安全環境。  不過，使用受保護的對等名稱無法確保網路應用程式的整體安全性。  應用程式的安全性與實作相關。  
  
 受保護的對等名稱由其擁有人只會註冊和保護公開金鑰加密。  受保護的對等名稱視為擁有由具有對等的實體對應的私密金鑰。  屬性可將已驗證的對等 Address \(CPA\) 證明，使用私密金鑰，簽署。  惡意使用者便偽造對等名稱的擁有權未對應的私密金鑰。  
  
## PNRP ID  
 ![PNRP ID](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.png "fdc9e8a0\-4a1c\-488d\-a019\-bc3a1973220c")  
  
 PNRP ID 撰寫如下:  
  
-   高位 128 位元，稱為對等 \(P2P\) ID，是對等名稱的雜湊指派給端點。  對等名稱的格式如下: *Authority.Classifier*。.  如果是受保護的名稱， *授權* 是對等名稱的公開金鑰的安全雜湊演算法 \(1\) SHA1 雜湊在十六進位字元。  對於不安全的名稱， *授權* 是單一字元「0 "。  分類器是識別應用程式中的字串。  對等名稱 Classifier 大於 149 個字元的長度不能大於，包括 `null` 結束字元。  
  
-   低位 128 位元用於服務位置使用，為產生的數字識別相同的 P2P ID 不同執行個體在同一個 Cloud 中。  
  
 接下來 ID 和服務位置的組合所允許多重 PNRP ID 從單一電腦登錄。  
  
## 請參閱  
 <xref:System.Net.PeerToPeer.PeerName>   
 <xref:System.Net.PeerToPeer>