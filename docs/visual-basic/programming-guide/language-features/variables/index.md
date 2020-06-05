---
title: 變數
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: ff617774d7e93ab4238ebc06617cc03fb6bc675a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410383"
---
# <a name="variables-in-visual-basic"></a>Visual Basic 中的變數
當您使用 Visual Basic 執行計算時，通常必須儲存值。 例如，您可能想要計算和比較數個值，並根據比較結果，對它們執行不同的作業。 如果您想要比較值，則必須保留值。  
  
## <a name="usage"></a>使用方式  
 Visual Basic，就像大部分的程式語言一樣，會使用變數來儲存值。 「變數」** 具有名稱 (您用來參考該變數所含值的字組)。 變數也具有資料類型 (可判斷該變數可儲存的資料類型)。 如果陣列必須儲存一組編製過索引的緊密相關資料項目，則變數可以代表陣列。  
  
 區域型別推斷可讓您宣告變數，而不需要明確陳述資料類型。 相反地，編譯器是根據初始化運算式的類型來推斷變數的類型。 如需詳細資訊，請參閱[區域型別推斷](local-type-inference.md)和 [Option Infer 陳述式](../../../language-reference/statements/option-infer-statement.md)。  
  
## <a name="assigning-values"></a>指派值  
 您可以使用指派陳述式來執行計算，並將結果指派給變數，如下列範例所示。  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> 在此範例中，等號 (`=`) 是指派運算子，不是等號比較運算子。 值將會指派給 `applesSold` 變數。  
  
 如需詳細資訊，請參閱[如何：移入和移出變數資料](how-to-move-data-into-and-out-of-a-variable.md)。  
  
## <a name="variables-and-properties"></a>變數和屬性  
 與變數類似，「屬性」** 代表您可存取的值。 不過，它比變數更為複雜。 屬性會使用程式碼區塊來控制如何設定和擷取其值。 如需詳細資訊，請參閱 [Visual Basic 中屬性和變數的差異](../procedures/differences-between-properties-and-variables.md)。  
  
## <a name="see-also"></a>另請參閱

- [變數宣告](variable-declaration.md)
- [物件變數](object-variables.md)
- [變數的疑難排解](troubleshooting-variables.md)
- [如何：移入和移出變數資料](how-to-move-data-into-and-out-of-a-variable.md)
- [Visual Basic 中屬性和變數的差異](../procedures/differences-between-properties-and-variables.md)
- [區域型別推斷](local-type-inference.md)
