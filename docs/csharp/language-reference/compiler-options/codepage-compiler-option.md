---
title: "/codepage (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/codepage"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/codepage compiler option [C#]"
  - "codepage compiler option [C#]"
  - "-codepage compiler option [C#]"
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /codepage (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

如果所需的頁面不是系統目前預設的字碼頁，這個選項可以指定編譯時使用的字碼頁。  
  
## 語法  
  
```  
/codepage:id  
```  
  
## Arguments  
 `id`  
 編譯過程中所有原始程式碼檔所使用字碼頁的 id。  
  
## 備註  
 如果您編譯一個或多個不是為了使用電腦上預設字碼頁而建立的原始程式碼檔，則可以使用 **\/codepage** 選項指定應該使用的字碼頁。  **\/codepage** 會套用到您所編譯的所有原始程式碼檔。  
  
 若原始程式檔是用您電腦內正在作用中的同一個字碼頁所建立的，或者原始程式檔是用 UNICODE 或 UTF\-8 所建立的，則您不需要使用 **\/codepage**。  
  
 如需關於搜尋系統所支援之字碼頁的資訊，請參閱 [GetCPInfo](http://go.microsoft.com/fwlink/?LinkId=148371) 。  
  
 在 Visual Studio 中無法使用這個編譯器選項，而且無法利用程式設計的方式變更它。  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)