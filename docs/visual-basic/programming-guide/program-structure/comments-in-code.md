---
title: "Comments in Code (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Uncomment button"
  - "REM statement"
  - "comments, in code"
  - "comments, Visual Basic code"
  - "Comment button"
  - "buttons, Uncomment"
  - "buttons, Comment"
  - "code comments, Visual Basic"
  - "Visual Basic code, comments"
  - "comments"
  - "code comments"
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Comments in Code (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

當您閱讀程式碼範例時，常會遇到註解符號 \(`'`\)。  這個符號會告知 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 編譯器忽略它後面的文字或「*註解*」\(Comment\)。  註解是為了閱讀者方便而加入至程式碼的簡短說明。  
  
 以簡短註解做為所有程序開頭是良好的程式設計作法，此註解會描述程序的基本特性 \(作用為何\)。  這對於您自己以及對於其他檢查程式碼的人都有好處。  您應該將描述功能特性的註解，與實作 \(Implementation\) 細節 \(程序是如何運作\) 分開。  當您將實作細節包含在描述中，請記得在更新函式時，將實作細節一同更新。  
  
 註解可以跟隨在陳述式之後的同一行中，或者佔據一整行。  兩者皆會在以下程式碼中加以說明。  
  
 [!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]  
  
 如果需要有一行以上的註解，請在每一行中使用註解符號，如下列範例：  
  
 [!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]  
  
## 註解方針  
 下表提供哪些註解類型可以出現在一段程式碼之前的一般方針。  這些都是建議，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 不會強制加入註解的規則。  撰寫對您自己與其他閱讀程式碼的人而言最有效的註解。  
  
|||  
|-|-|  
|註解類型|註解說明|  
|用途|描述程序的功用 \(非如何運作\)|  
|假設|列出每個外部變數、控制項、開啟檔案或其他程序存取的項目|  
|效果|列出每個受影響的外部變數、控制項或檔案，以及其所受的影響 \(僅限於不明顯的\)|  
|輸入|指定引數的用途|  
|Returns|說明程序傳回的值|  
  
 請記住以下要點：  
  
-   每個重要的變數宣告之前都應該有註解，此註解會描述所宣告之變數的用途。  
  
-   變數、控制項和程序應該清楚命名，讓註解只需用於複雜的實作細節中。  
  
-   註解不可以跟隨在同一行的行接續序列之後。  
  
 您可以藉由選取一或多行程式碼，並選擇 \[**編輯**\] 工具列中的 \[**註解**\]  \(![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")\) 和 \[**註解排除**\]\(![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.png "vaUncommentButton")\) 按鈕，加入或移除一個程式碼區段的註解符號。  
  
> [!NOTE]
>  您也可以藉由在文字前方置入 `REM` 關鍵字，將註解加入至您的程式碼中。  然而，`'` 符號和 \[**註解**\] \/ \[**取消註解**\] 按鈕比較容易使用，而且需要的空間與記憶體較少。  
  
## 請參閱  
 [使用 XML 註解記錄程式碼](http://msdn.microsoft.com/magazine/dd722812.aspx)   
 [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)   
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)   
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [REM Statement](../../../visual-basic/language-reference/statements/rem-statement.md)