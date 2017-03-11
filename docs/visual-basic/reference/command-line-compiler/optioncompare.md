---
title: "/optioncompare | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/optioncompare"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "optioncompare compiler option [Visual Basic]"
  - "-optioncompare compiler option [Visual Basic]"
  - "/optioncompare compiler option [Visual Basic]"
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# /optioncompare
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定如何進行字串比較。  
  
## 語法  
  
```  
/optioncompare:{binary | text}  
```  
  
## 備註  
 您可指定其中一種格式的 `/optioncompare`：`/optioncompare:binary` 可使用二進位字串比較，而 `/optioncompare:text` 則使用文字字串比較。  編譯器 \(Compiler\) 預設會使用 `/optioncompare:binary`。  
  
 在 Microsoft Windows 中，使用中的字碼頁 \(Code Page\) 可以決定二進位排序次序。  以下是一般的二進位排序順序：  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 以文字為主的字串比較，是以您系統地區設定所決定的不區分大小寫文字排序次序為基礎。  以下是一般的文字排序順序：  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### 若要在 Visual Studio IDE 中設定 \/optioncompare  
  
1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 \[**編譯**\] 索引標籤。  
  
3.  修改 \[**Option Compare**\] 方塊中的值。  
  
### 若要以程式設計方式設定 \/optioncompare  
  
-   請參閱 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)。  
  
## 範例  
 下列程式碼會編譯 P`rojFile.vb`，並使用二進位字串比較。  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [選項對話方塊、專案、Visual Basic 預設值](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)