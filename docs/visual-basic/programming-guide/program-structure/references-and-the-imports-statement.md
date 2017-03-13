---
title: "References and the Imports Statement (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "assemblies [Visual Basic], namespaces"
  - "references, assembly"
  - "namespaces, assemblies"
  - "referencing assemblies"
  - "Imports statement, referencing assemblies"
  - "assemblies [Visual Basic], references"
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# References and the Imports Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

您可在 \[**專案**\] 功能表中選擇 \[**加入參考**\] 命令，讓您的專案能夠使用外部物件。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的參考可指向組件 \(Assembly\)，這些組件與型別程式庫 \(Type Library\) 類似，但包含更多的資訊。  
  
## Imports 陳述式  
 組件包括一個或多個命名空間。  將參考加入組件中時，您也可以將 `Imports` 陳述式 \(Statement\) 加入控制模組內部組件命名空間的可見度的模組中。  `Imports` 陳述式提供的內容範圍設定，讓您能夠只使用必要的部分命名空間就能提供特別的參考。  
  
 `Imports` 陳述式有下列語法：  
  
 `Imports` \[         `|` `Aliasname` \=\] `Namespace`  
  
 `Aliasname` 是指您可在程式碼內使用以參考匯入之命名空間的簡短名稱。  `Namespace` 是透過專案參考、專案內的定義或上一個 `Imports` 陳述式取得的命名空間。  
  
 模組可包含任何數目的 `Imports` 陳述式。  它們必須出現在任何 `Option` 陳述式之後，但在任何其他程式碼之前。  
  
> [!NOTE]
>  不要將專案參考與 `Imports` 陳述式或 `Declare` 陳述式混淆。  專案參考可讓 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 專案使用外部物件，例如組件中的物件。  `Imports` 陳述式是用來簡化專案參考的存取，但不提供對這些物件的存取。  `Declare` 陳述式是用來宣告對動態連結程式庫 \(DLL\) 中外部程序的參考。  
  
## 以 Imports 陳述式使用別名  
 `Imports` 陳述式讓您不需要明確地輸入參考的完整名稱，就可以更容易地存取類別 \(Class\) 中的方法。  別名 \(Alias\) 可讓您只對命名空間的一部分指派較簡易的名稱。  例如，導致一段文字以多行顯示的歸位字元 \(Carriage Return\)\/換行字元 \(Line Feed\) 循序項 \(Sequence\)，是 <xref:Microsoft.VisualBasic?displayProperty=fullName> 命名空間中 <xref:Microsoft.VisualBasic.ControlChars> 模組的一部分。  若不以別名在程式中使用這個常數，您需要輸入下列程式碼：  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports` 陳述式必須緊接在模組中任何 `Option` 陳述式之後的第一行。  下列程式碼片段會顯示如何將別名匯入和指派給 <xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName> 模組：  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 未來對這個命名空間的參考可以非常簡短：  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 如果 `Imports` 陳述式不包括別名名稱，該匯入命名空間內定義的項目不需完整名稱就可在模組中使用。  如果有指定別名名稱，就必須做為該命名空間內所含的名稱限定詞 \(Qualifier\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ControlChars>   
 <xref:Microsoft.VisualBasic>   
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [組件和全域組件快取](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [如何：使用命令列建立和使用組件](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)