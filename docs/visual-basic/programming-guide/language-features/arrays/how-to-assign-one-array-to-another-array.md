---
title: 如何：指派一個陣列至另一個陣列 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 63c7d187152fcb5ea84378c677aa687f334f63de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647926"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>如何：指派一個陣列至另一個陣列 (Visual Basic)
因為陣列是物件，您可以使用類似其他物件類型的指派陳述式中。 陣列變數會保留從屬陣列元素和的順位和長度的資訊，將資料指標，並指派複製只有這個指標。  
  
### <a name="to-assign-one-array-to-another-array"></a>若要指派一個陣列至另一個陣列  
  
1.  請確定這兩個陣列都具有相同的陣序 （維度數目） 和相容的項目資料類型。  
  
2.  使用標準的指派陳述式，將來源陣列指派到目的地陣列。 務必按照陣列名稱加上括弧。  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 當您指派一個陣列至另一個時，適用下列規則：  
  
-   **相同的陣序規範。** 目的陣列的陣序 （維度數目） 必須與來源陣列的相同。  
  
     提供兩個陣列的陣序規範相等，不需要相同維度。 指定維度中的項目數可以在指派期間變更。  
  
-   **項目型別。** 這兩個陣列必須有*參考型別*項目或兩個陣列必須有*實值型別*項目。 如需詳細資訊，請參閱[實值類型和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
    -   如果這兩個陣列都具有值型別項目，項目資料類型必須完全相同。 唯一的例外是您可以指派的陣列`Enum`的基底的類型陣列的項目`Enum`。  
  
    -   如果這兩個陣列都具有型別元素的參考，來源項目類型必須衍生自目的項目型別。 這種情況時，兩個陣列都具有相同的繼承關聯性，做為其項目。 這稱為*陣列共變數*。  
  
 編譯器會報告錯誤若違反上述規則，例如如果資料類型不相容或陣序規範不相等。 您可以加入錯誤處理以將您的程式碼，請確定陣列相容，然後再嘗試指派。 您也可以使用[TryCast 運算子](../../../../visual-basic/language-reference/operators/trycast-operator.md)關鍵字，如果您想要避免擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [陣列的疑難排解](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Enum 陳述式](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
