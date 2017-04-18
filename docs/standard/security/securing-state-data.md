---
title: "Securing State Data | Microsoft Docs"
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
  - "security [.NET Framework], state data"
  - "code security, state data"
  - "secure coding, state data"
  - "state data security"
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# Securing State Data
處理敏感資料或執行任何種類的安全性決策的應用程式都必須使這些資料保持在它們自己的控制下，而且不能允許其他潛在的惡意程式碼直接存取這些資料。  保護記憶體中資料的最佳做法，是將資料宣告為私用 \(Private\) 或內部 \(範圍限於相同的組件內\) 變數。  然而，雖然這些資料的存取受到限制，但您還是應該留意：  
  
-   高度受信任的程式碼能夠參考您的物件，它還可以使用反映 \(Reflection\) 機制來取得及設定私用成員。  
  
-   如果高度受信任的程式碼可以存取物件的序列化形式的對應資料，它就可以使用序列化 \(Serialization\) 有效取得及設定私用成員。  
  
-   偵錯進行中，這項資料可以被讀取。  
  
 請確認您自己的方法或屬性都不會意外公開這些值。  
  
 在某些情況下，您可以將資料宣告為「受保護」，並將存取權限制成只能存取類別和它的衍生物件。  然而，由於額外的公開狀況，您還必須採取下列額外防範措施：  
  
-   將程式碼限制在相同的組件中以控制可以從您的類別衍生的程式碼，或是使用[設定方法存取的安全性](../../../docs/framework/misc/securing-method-access.md)中說明的宣告式安全性，來要求某種識別 \(Identity\) 或某些使用權限，使其可以從您的類別衍生。  
  
-   確定所有衍生類別 \(Derived Class\) 全都實作類似的保護或是都已密封。  
  
## 請參閱  
 [Secure Coding Guidelines](../../../docs/standard/security/secure-coding-guidelines.md)