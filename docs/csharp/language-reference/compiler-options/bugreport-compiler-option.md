---
title: "/bugreport (C# Compiler Options) | Microsoft Docs"
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
  - "/bugreport"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/bugreport compiler option [C#]"
  - "-bugreport compiler option [C#]"
  - "bugreport compiler option [C#]"
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /bugreport (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定偵錯資訊應該置於檔案以便稍後分析。  
  
## 語法  
  
```  
/bugreport:file  
```  
  
## 引數  
 `file`  
 您要包含錯誤報告的檔案名稱。  
  
## 備註  
 **\/bugreport** 選項會指定下列資訊應該置於 `file`：  
  
-   編譯中所有原始程式碼檔的複本。  
  
-   編譯中使用的編譯器選項清單。  
  
-   您的編譯器、執行階段和作業系統的版本資訊。  
  
-   除了隨附於 .NET Framework 和 SDK 的組件之外，還包括參考組件和模組 \(儲存為十六進位數字\)。  
  
-   編譯器輸出 \(如果有的話\)。  
  
-   問題的描述，會提示您操作指示。  
  
-   您認為問題該如何解決的描述，會提示您操作指示。  
  
 如果搭配 **\/errorreport:prompt** 或 **\/errorreport:send** 使用這個選項，檔案中的資訊會傳送到 Microsoft Corporation。  
  
 由於 `file` 中放置所有原始程式碼檔的複本，您可能想要以最短的可能程式重現 \(可疑的\) 程式碼缺失。  
  
 在 Visual Studio 中無法使用這個編譯器選項，而且無法利用程式設計的方式變更它。  
  
 請注意，所產生檔案的內容會公開 \(Expose\) 原始程式碼，而這可能會不慎洩漏資訊。  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [\/errorreport \(Set Error Reporting Behavior\)](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)