---
title: HOW TO：指派一個陣列至另一個陣列 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 78497de3a9aea55320639c55a151a1260a960159
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303085"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>HOW TO：指派一個陣列至另一個陣列 (Visual Basic)
因為陣列是物件，您可以像其他物件類型的指派陳述式中使用它們。 陣列變數會保留構成的陣列項目和的順位和長度的資訊，將資料指標，並指派複製只有此指標。  
  
### <a name="to-assign-one-array-to-another-array"></a>若要指派一個陣列至另一個陣列  
  
1. 請確定兩個陣列具有相同陣序 （維度數目） 和相容的項目資料型別。  
  
2. 您可以使用標準的指派陳述式，將來源陣列指派給目的地陣列。 請勿遵循任一陣列名稱，加上括弧。  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 當您指派一個陣列至另一個時，適用下列規則：  
  
-   **相同的陣序規範。** 目的陣列的陣序 （維度數目） 必須是相同的來源陣列。  
  
     提供兩個陣列的陣序規範是相等的不需要相同維度。 指定維度中的項目數可以在指派期間變更。  
  
-   **項目型別。** 可能是這兩個陣列必須有*參考的型別*項目或兩個陣列必須*實值型別*項目。 如需詳細資訊，請參閱 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
    -   如果兩個陣列值型別項目，項目資料類型必須完全相同。 唯一的例外是，您可以將指派的陣列`Enum`的基底型別陣列的項目`Enum`。  
  
    -   如果兩個陣列都具有參考型別項目，將來源項目型別必須衍生自目的項目型別中。 這種情況時，兩個陣列都具有相同的繼承關聯性，做為其項目。 這就叫做*陣列共變數*。  
  
 編譯器會報告錯誤，如果違反上述規則，例如如果資料類型不相容或陣序規範不相等。 您可以新增錯誤處理您的程式碼，請確定陣列相容，然後再嘗試指派。 您也可以使用[TryCast 運算子](../../../../visual-basic/language-reference/operators/trycast-operator.md)關鍵字，如果您想要避免擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱

- [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [針對陣列進行疑難排解](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Enum 陳述式](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
