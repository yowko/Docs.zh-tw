---
title: "/warnaserror (C# Compiler Options) | Microsoft Docs"
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
  - "/warnaserror"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/warnaserror compiler option [C#]"
  - "-warnaserror compiler option [C#]"
  - "warnaserror compiler option [C#]"
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /warnaserror (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/warnaserror\+** 選項會將所有警告視為錯誤。  
  
## 語法  
  
```  
/warnaserror[<U>+</U> | -][:warning-list]  
```  
  
## 備註  
 任何原本報告為警告的訊息將以錯誤報告，並中止 \(不建置輸出檔\) 建置處理。  
  
 根據預設，**\/warnaserror\-** 為作用中，可使警告不至於防止輸出檔的產生。  **\/warnaserror** 和 **\/warnaserror\+** 一樣，會將警告視為錯誤。  
  
 如果您只要將少數的特定警告視為錯誤，可以選擇指定逗號分隔的清單，列出要視為錯誤的警告編號。  
  
 使用 [\/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) 指定您要編譯器顯示的警告層級。  使用 [\/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) 停用某些警告。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**建置**\] 屬性頁。  
  
3.  修改 \[**警告視為錯誤**\] 屬性。  
  
     若要用程式設計的方式設定這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>。  
  
## 範例  
 編譯 `in.cs` 並讓編譯器停止顯示任何警告：  
  
```  
csc /warnaserror in.cs  
csc /warnaserror:642,649,652 in.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)