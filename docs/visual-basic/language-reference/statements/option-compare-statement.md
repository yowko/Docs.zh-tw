---
title: "Option Compare Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Compare"
  - "vb.OptionCompare"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "case sensitivity, Option Compare statement"
  - "Compare keyword"
  - "binary comparison"
  - "strings [Visual Basic], returning from functions"
  - "binary comparison, Option Compare statement"
  - "strings [Visual Basic], comparing"
  - "string comparison [Visual Basic], Option Compare statement"
  - "Text keyword, Option Compare statement"
  - "Binary keyword, Option Compare statement"
  - "string comparison [Visual Basic], sorting data"
  - "Option Compare statement"
  - "text [Visual Basic], comparing"
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: 37
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 37
---
# Option Compare Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Declares the default comparison method to use when comparing string data.  
  
## 語法  
  
```  
Option Compare { Binary | Text }  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`Binary`|選擇項。  Results in string comparisons based on a sort order derived from the internal binary representations of the characters.<br /><br /> This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.  In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.|  
|`Text`|選擇項。  Results in string comparisons based on a case\-insensitive text sort order determined by your system's locale.<br /><br /> This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.  For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.|  
  
## 備註  
 If used, the `Option Compare` statement must appear in a file before any other source code statements.  
  
 The `Option Compare` statement specifies the string comparison method \(`Binary` or `Text`\).  The default text comparison method is `Binary`.  
  
 A `Binary` comparison compares the numeric Unicode value of each character in each string.  A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.  
  
 In Microsoft Windows, sort order is determined by the code page.  如需詳細資訊，請參閱[字碼頁](/visual-cpp/c-runtime-library/code-pages)。  
  
 在下列範例中，英文\/歐語系字碼頁 \(ANSI 1252\) 中的字元是使用 `Option Compare Binary` 來排序，這會產生一般的二進位排序順序。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 使用 `Option Compare Text` 排序相同字碼頁中的相同字元時，會產生下列的文字排序順序。  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## Option Compare 陳述式不存在時  
 如果原始程式碼不包含 `Option Compare` 陳述式，會使用[專案設計工具、編譯頁 \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)上的 \[選項比較\] 設定。  如果您使用命令列編譯器，則會使用 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) 編譯器選項所指定的設定。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
#### 在 IDE 中設定選項比較  
  
1.  在 \[方案總管\] 中選取專案。  在 \[專案\] 功能表上，按一下 \[屬性\]。  如需詳細資訊，請參閱[NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/zh-tw/983f3c18-832f-4666-afec-74b716ff3e0e)。  
  
2.  按一下 \[編譯\] 索引標籤。  
  
3.  在 \[選項比較\] 方塊中設定值。  
  
 當您建立專案時，\[編譯\] 索引標籤上的 \[選項比較\] 設定會設定為 \[選項\] 對話方塊中的 \[選項比較\] 設定。  若要變更此設定，請在 \[工具\] 功能表上按一下 \[選項\]。  在\[選項\] 對話方塊中，展開 \[專案和方案\]，然後按一下 \[VB 預設值\]。  \[VB 預設值\] 中的初始預設設定是 \[二進位\]。  
  
#### 在命令列上設定選項比較  
  
-   在 **vbc** 命令中併入 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) 編譯器選項。  
  
## 範例  
 下列範例會使用 `Option Compare` 陳述式來將二進位比較設為預設字串比較方法。  若要使用這段程式碼，請取消註解 `Option Compare Binary` 陳述式，並將其放置在原始程式檔的頂端。  
  
 [!code-vb[VbVbalrStatements#45](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]  
  
## 範例  
 下列範例會使用 `Option Compare` 陳述式，將不區分大小寫文字排序順序設定為預設字串比較方法。  若要使用這段程式碼，請取消註解 `Option Compare Text` 陳述式，並將其放置在原始程式檔的頂端。  
  
 [!code-vb[VbVbalrStatements#46](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>   
 <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>   
 <xref:Microsoft.VisualBasic.Strings.Replace%2A>   
 <xref:Microsoft.VisualBasic.Strings.Split%2A>   
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md)   
 [字串函式](../../../visual-basic/language-reference/functions/string-functions.md)   
 [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)