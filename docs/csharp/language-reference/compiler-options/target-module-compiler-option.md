---
title: "/target:module (C# Compiler Options) | Microsoft Docs"
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
  - "/target:module"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-target compiler options [C#], /target:module"
  - "target compiler options [C#], /target:module"
  - "/target compiler options [C#], /target:module"
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:module (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

這個選項可讓編譯器不產生組件資訊清單 \(Assembly Manifest\)。  
  
## 語法  
  
```  
/target:module  
```  
  
## 備註  
 根據預設，使用這個選項編譯時，所建立的輸出檔具有副檔名 .netmodule。  
  
 .NET Framework Common Language Runtime 無法載入不具有組件資訊清單的檔案。  不過，這種檔案可以透過 [\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md)，合併至某個組件的組件資訊清單中。  
  
 如果單一編譯建立的模組超過一個，則某個模組內的 [internal](../../../csharp/language-reference/keywords/internal.md) 型別也可以在編譯時供其他模組使用。  當某個模組的程式碼參考到其他模組的 `internal` 型別時，兩個模組就必須透過 **\/addmodule** 合併至組件資訊清單。  
  
 Visual Studio 開發環境中不支援建立模組。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## 範例  
 編譯 `in.cs` 並建立 `in.netmodule`：  
  
```  
csc /target:module in.cs  
```  
  
## 請參閱  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)