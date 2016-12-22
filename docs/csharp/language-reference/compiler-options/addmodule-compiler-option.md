---
title: "/addmodule (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/addmodule"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/addmodule compiler option [C#]"
  - "-addmodule compiler option [C#]"
  - "addmodule compiler option [C#]"
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /addmodule (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

這個選項會將使用 target:module 參數建立的模組加入目前的編譯中。  
  
## 語法  
  
```  
/addmodule:file[;file2]  
```  
  
## 引數  
 `file`, `file2`  
 包含中繼資料 \(Metadata\) 的輸出檔。  此檔案不能包含組件資訊清單 \(Assembly Manifest\)，  若要匯入一個以上檔案，請以逗號或分號區隔檔案名稱。  
  
## 備註  
 所有用 **\/addmodule** 加入的模組，必須與執行階段時的輸出檔位在相同的目錄。  也就是說，您可以在編譯時期指定任一目錄中的模組，但是該模組在執行階段時，必須在應用程式目錄中。  如果此模組於執行階段時不在應用程式目錄中，您便會收到 <xref:System.TypeLoadException>。  
  
 `file` 不能包含組件。  例如，如果使用 [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 建立了輸出檔，它的中繼資料便可以使用 **\/addmodule** 來匯入。  
  
 如果使用 **\/target** 選項，而不是 **\/target:module** 建立輸出檔，它的中繼資料便無法使用 **\/addmodule** 來匯入，但是可以使用 [\/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) 來匯入。  
  
 這個編譯器選項無法在 Visual Studio 中使用；專案無法參考到模組。  此外，這個編譯器選項無法以程式設計的方式變更。  
  
## 範例  
 編譯 `input.cs` 原始程式檔 \(Source File\)，並從 `metad1.netmodule` 和 `metad2.netmodule` 加入中繼資料以產生 `out.exe`：  
  
```  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [多檔案組件](../Topic/Multifile%20Assemblies.md)   
 [如何：建置多檔案組件](../Topic/How%20to:%20Build%20a%20Multifile%20Assembly.md)