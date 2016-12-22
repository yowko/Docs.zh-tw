---
title: "/nowarn (C# Compiler Options) | Microsoft Docs"
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
  - "/nowarn"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "nowarn compiler option [C#]"
  - "/nowarn compiler option [C#]"
  - "-nowarn compiler option [C#]"
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /nowarn (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/nowarn** 選項可讓編譯器隱藏一個或多個警告。  使用逗號來區隔多個警告編號。  
  
## 語法  
  
```  
/nowarn:number1[,number2,...]  
```  
  
## 引數  
 `number1`, `number2`  
 您要編譯器隱藏的警告編號。  
  
## 備註  
 您只需要指定警告識別項的數字部分。  例如，如果您要隱藏 CS0028，您可以指定 `/nowarn:28`。  
  
 如果傳遞至 `/nowarn` 的警告編號在先前的版本中為有效時，且已經從編譯器移除的話，編譯器將會自動忽略這些警告編號。  例如，CS0679 對於 Visual Studio .NET 2002 的編譯器而言是有效的，但隨後就會被移除。  
  
 `/nowarn` 選項無法隱藏下列警告：  
  
-   編譯器警告 \(層級 1\) CS2002  
  
-   編譯器警告 \(層級 1\) CS2023  
  
-   編譯器警告 \(層級 1\) CS2029  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  如需詳細資訊，請參閱 [專案設計工具、建置頁 \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp)。  
  
2.  按一下 \[**建置**\] 屬性頁。  
  
3.  修改 \[**隱藏警告**\] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>。  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [C\# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md)