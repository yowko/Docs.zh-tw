---
title: "/target:library (C# Compiler Options) | Microsoft Docs"
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
  - "/dll"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-target compiler options [C#], /target:library"
  - "target compiler options [C#], /target:library"
  - "/target compiler options [C#], /target:library"
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:library (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/target:library** 選項會讓編譯器建立動態連結程式庫 \(DLL\)，而非執行檔 \(EXE\)。  
  
## 語法  
  
```  
/target:library  
```  
  
## 備註  
 DLL 會以 .dll 副檔名建立。  
  
 除非您已使用 [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔名稱，否則將會以第一個輸入檔名稱命名。  
  
 在命令列上指定時，直到下一個 **\/out** 或 **\/target:module** 選項的所有檔案都會用來建立 .dll 檔案。  
  
 建置 .dll 檔時並不需要 [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) 方法。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**應用程式**\] 屬性頁。  
  
3.  修改 \[**輸出類型**\] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## 範例  
 編譯 `in.cs` 並建立 `in.dll`：  
  
```  
csc /target:library in.cs  
```  
  
## 請參閱  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)