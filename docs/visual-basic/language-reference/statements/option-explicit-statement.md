---
title: "Option Explicit Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Explicit"
  - "vb.OptionExplicit"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declaring variables, explicit"
  - "forced variable declaration in Option Explicit statement"
  - "Explicit keyword"
  - "explicit variable declaration"
  - "Option Explicit statement"
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Option Explicit Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

強制明確宣告檔案中的所有變數，或者允許隱含宣告變數。  
  
## 語法  
  
```  
Option Explicit { On | Off }  
```  
  
## 組件  
 `On`  
 選擇項。  啟用 `Option Explicit` 檢查。  如果未指定 `On` 或 `Off`，則預設值為 `On`。  
  
 `Off`  
 選擇項。  停用 `Option Explicit` 檢查。  
  
## 備註  
 當 `Option Explicit On` 或 `Option Explicit` 出現在檔案中時，您必須使用 `Dim` 或 `ReDim` 陳述式明確宣告所有變數。  如果嘗試使用未宣告的變數名稱，便會在編譯時期發生錯誤。  `Option Explicit Off` 陳述式允許隱含宣告變數。  
  
 如果使用，在檔案中 `Option Explicit` 陳述式必須出現在任何其他原始程式碼陳述式之前。  
  
> [!NOTE]
>  將 `Option Explicit` 設定為 `Off` 通常不是良好的做法。  一個或多個位置中的變數名稱可能有拼字錯誤，這會在程式執行時造成非預期的結果。  
  
## 當 Option Explicit 陳述式不存在時  
 如果原始程式碼不包含 `Option Explicit` 陳述式，則會使用 [專案設計工具、編譯頁 \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) 上的 \[**Option Explicit**\] 設定。  如果使用命令列編譯器，就會使用 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) 編譯器選項。  
  
#### 若要在 IDE 中設定 Option Explicit  
  
1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 \[**編譯**\] 索引標籤。  
  
3.  設定 \[**Option Explicit**\] 方塊中的值。  
  
 當您建立新專案時，\[**編譯**\] 索引標籤上的 \[**Option Explicit**\] 會設定為 \[**VB 預設值**\] 對話方塊中的 \[**Option Explicit**\] 設定。  若要存取 \[**VB 預設值**\] 對話方塊，請在 \[**工具**\] 功能表中按一下 \[**選項**\]。  在 \[**選項**\] 對話方塊中，展開 \[**專案和方案**\]，然後按一下 \[**VB 預設值**\]。  \[**VB 預設值**\] 中的初始預設設定是 `On`。  
  
#### 若要在命令列上設定 Option Explicit  
  
-   在 **vbc** 命令中包含 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) 編譯器選項。  
  
## 範例  
 下列範例會使用 `Option Explicit` 陳述式，強制明確宣告所有的變數。  嘗試使用未宣告的變數會在編譯時期引發錯誤。  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/option-explicit-statement_2.vb)]  
  
## 請參閱  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [選項對話方塊、專案、Visual Basic 預設值](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)