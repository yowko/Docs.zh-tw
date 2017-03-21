---
title: "如何︰ 中斷和合併陳述式在程式碼 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb._
dev_langs:
- VB
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores, in code
- statements [Visual Basic], line continuation in
- line breaks, in code
- line-continuation character
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
caps.latest.revision: 21
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 840036a91f430f72e0258b8be466770f2855a58f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>如何：在程式碼中中斷和合併陳述式 (Visual Basic)
在撰寫程式碼時，您有時可能會建立冗長的陳述式的水平捲軸在程式碼編輯器。 雖然這並不會影響的方式執行程式碼，它不容易為您或其他人的監視器上顯示的方式，閱讀程式碼。 在這種情況下，您應該考慮分為數行的一個長陳述式。  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>若要在單一陳述式分成多行程式碼  
  
-   使用行接續字元，也就是底線 (`_`)，想要中斷的行之處。 底線的前面必須緊接一個空格，後面則必須緊接著行結束字元 (歸位字元)。  
  
    > [!NOTE]
    >  在某些情況下，如果您省略行接續字元 Visual Basic 編譯器會隱含地繼續陳述式在下一行程式碼。 可以略過的行接續字元的語法項目清單，請參閱 「 隱含行接續符號 」，在[陳述式](../../../visual-basic/programming-guide/language-features/statements.md)。  
  
     在下列範例中，陳述式會分成四行程式碼，以終止所有的行接續字元，但最後一行。  
  
     [!code-vb[VbVbcnConventions #&20;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     使用此順序可讓您的程式碼更方便閱讀，列印線上和時。  
  
     行接續字元必須是在一行的最後一個字元。 您不能與任何其他項目跟隨它在同一行。  
  
     有關您可以在其中使用行接續字元中，有部分限制例如，您無法使用它的引數名稱中間。 您可以中斷引數清單使用行接續符號的字元，但個別引數的名稱必須保持不變。  
  
     您無法繼續註解使用行接續字元。 編譯器不會檢查有特殊意義的註解中的字元。 多行註解，重複執行註解符號 (`'`) 在每一行。  
  
 雖然個別行上放置每個陳述式是建議的方法，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]也可讓您將多個陳述式放在同一行。  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>若要在同一行上放置多個陳述式  
  
-   將陳述式以冒號分隔 (`:`)，如下列範例所示。  
  
     [!code-vb[VbVbcnConventions #&10;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
