---
title: Visual Basic 中的變數
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7a47ad7e4ade9f15159c27ac672aeb937a05493
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="variables-in-visual-basic"></a>Visual Basic 中的變數
當您使用 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 執行計算時，通常需要儲存值。 例如，您可能想要計算和比較數個值，並根據比較結果，對它們執行不同的作業。 如果您想要比較值，則必須保留值。  
  
## <a name="usage"></a>使用方式  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]，就像大多數的程式設計語言，都會使用變數來儲存值。 「變數」具有名稱 (您用來參考該變數所含值的字組)。 變數也具有資料類型 (可判斷該變數可儲存的資料類型)。 如果陣列必須儲存一組編製過索引的緊密相關資料項目，則變數可以代表陣列。  
  
 區域型別推斷可讓您宣告變數，而不需要明確陳述資料類型。 相反地，編譯器是根據初始化運算式的類型來推斷變數的類型。 如需詳細資訊，請參閱[區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)和 [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。  
  
## <a name="assigning-values"></a>指派值  
 您可以使用指派陳述式來執行計算，並將結果指派給變數，如下列範例所示。  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  在此範例中，等號 (`=`) 是指派運算子，不是等號比較運算子。 值將會指派給 `applesSold` 變數。  
  
 如需詳細資訊，請參閱[如何：移入和移出變數資料](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)。  
  
## <a name="variables-and-properties"></a>變數和屬性  
 與變數類似，「屬性」代表您可存取的值。 不過，它比變數更為複雜。 屬性會使用程式碼區塊來控制如何設定和擷取其值。 如需詳細資訊，請參閱 [Visual Basic 中屬性和變數的差異](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)。  
  
## <a name="see-also"></a>另請參閱  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [變數的疑難排解](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)  
 [如何：移入和移出變數資料](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [在 Visual Basic 中屬性和變數之間的差異](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)  
 [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
