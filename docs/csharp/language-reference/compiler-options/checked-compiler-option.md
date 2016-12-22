---
title: "/checked (C# Compiler Options) | Microsoft Docs"
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
  - "/checked"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "checked compiler option [C#]"
  - "-checked compiler option [C#]"
  - "/checked compiler option [C#]"
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /checked (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/checked** 選項會指定產生超出資料型別範圍 \(Range\) 之值，且不在 [checked](../../../csharp/language-reference/keywords/checked.md) 或 [unchecked](../../../csharp/language-reference/keywords/unchecked.md) 關鍵字範圍 \(scope\) 內的整數算術陳述式，是否要執行階段例外狀況。  
  
## 語法  
  
```  
/checked[+ | -]  
```  
  
## 備註  
 在 `checked` 或 `unchecked` 關鍵字範圍內的整數算術陳述式並不受 **\/checked** 選項的影響。  
  
 如果不在 `checked` 或 `unchecked` 關鍵字範圍內的整數算術陳述式會產生超出資料型別範圍的值，而且在編譯中使用 **\/checked\+** \(**\/checked**\)，則該陳述式會在執行階段造成例外狀況。  如果在編譯中使用 **\/checked\-**，該陳述式就不會在執行階段時產生例外狀況。  
  
 這個選項的預設值是 **\/checked\-**。  使用**\/checked\-**的其中一個案例是組建大型應用程式。  有時會使用自動化工具組建此類應用程式，且此類工具可能會將 **\/checked** 設為 \+。  您可以指定 **\/checked\-** 來覆寫工具的全域預設值。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  如需詳細資訊，請參閱 [專案設計工具、建置頁 \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp)。  
  
2.  按一下 \[**建置**\] 屬性頁。  
  
3.  按一下 \[**進階**\] 按鈕。  
  
4.  修改 \[**檢查算術溢位\/反向溢位**\] 屬性。  
  
 若要以程式設計的方式存取這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>。  
  
## 範例  
 下列命令會編譯 `t2.cs`。  在命令中使用 `/checked`，會指定檔案中不在 `checked` 或 `unchecked` 關鍵字範圍內 \(且會產生超出該資料型別範圍的值\) 的任何整數算術陳述式，都要在執行階段產生例外狀況。  
  
```  
csc t2.cs /checked  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)