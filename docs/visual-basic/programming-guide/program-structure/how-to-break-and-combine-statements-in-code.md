---
title: 如何：在程式碼中中斷和合併陳述式 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb._
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
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06702cdc9073065a418b17d198dbb43be4aefca1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>如何：在程式碼中中斷和合併陳述式 (Visual Basic)
撰寫程式碼，就表示您有時候可能會建立冗長且必須水平捲軸在程式碼編輯器中的陳述式。 雖然這不會影響的方式執行程式碼，但是它困難為您或其他人閱讀的程式碼，因為它會出現在監視器。 在這種情況下，您應該考慮分為數行的單一長陳述式。  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>若要在單一陳述式分成多行  
  
-   使用行接續字元是底線 (`_`)，在想要中斷線條的點。 底線的前面必須緊接一個空格，後面則必須緊接著行結束字元 (歸位字元)。  
  
    > [!NOTE]
    >  在某些情況下，如果您省略行接續字元中，Visual Basic 編譯器會隱含地繼續陳述式在下一行程式碼。 如需可以略過行接續字元的語法項目，請參閱 「 隱含行接續符號 」 中[陳述式](../../../visual-basic/programming-guide/language-features/statements.md)。  
  
     在下列範例中，陳述式會分成四行終止所有的行接續字元，但最後一行。  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     使用此順序可讓您的程式碼更方便閱讀，列印線上和時。  
  
     行接續字元必須是該行的最後一個字元。 您不可以跟隨它與其他任何項目在同一行。  
  
     某些限制存有您可以在其中使用行接續字元。比方說，您無法使用它的引數名稱中間。 您可能會中斷以行接續字元的引數清單，但引數的個別名稱必須保持不變。  
  
     您無法繼續註解使用行接續字元。 編譯器不會檢查特殊意義的註解中的字元。 多行註解，針對重複的註解符號 (`'`) 在每一行。  
  
 雖然建議的方法是將每個陳述式放在不同行，Visual Basic 也可讓您將多個陳述式放在同一行。  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>若要將多個陳述式放在同一行  
  
-   以冒號分隔的陳述式 (`:`)，如下列範例所示。  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
