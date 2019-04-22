---
title: 遮蔽和覆寫的差異 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: b935184f0e4d0378bfea69811aa4e6c068a9776f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827922"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>遮蔽和覆寫的差異 (Visual Basic)
當您定義繼承自基底類別的類別時，您有時會想要重新定義一或多個基底類別中的項目衍生的類別。 遮蔽和覆寫都可針對此目的。  
  
## <a name="comparison"></a>邏輯比對  
 遮蔽和覆寫同時使用當在衍生的類別繼承自基底類別，並同時重新定義與另一個宣告的項目。 但兩者之間有顯著的差異。  
  
 下表比較遮蔽和覆寫。  
  
||||  
|---|---|---|  
|相較之下|遮蔽|覆寫|  
|用途|防止後續的基底類別修改，將會介紹您已定義在衍生類別中的成員|藉由定義的程序或屬性具有相同的呼叫順序的不同實作，達到多型<sup>1</sup>|  
|已重新定義的項目|任何宣告項目類型|程序 (`Function`， `Sub`，或`Operator`) 或屬性|  
|重新定義的項目|任何宣告項目類型|只有程序或屬性具有相同的呼叫順序<sup>1</sup>|  
|存取層級的重新定義項目|任何存取層級|無法變更存取層級覆寫的項目|  
|可讀性和可寫性的重新定義項目|任何組合|無法變更可讀性或可寫性的覆寫的屬性|  
|重新定義的控制|基底類別項目無法強制執行，或禁止的遮蔽功能|基底類別項目可以指定`MustOverride`， `NotOverridable`，或 `Overridable`|  
|關鍵字的使用方式|`Shadows` 在衍生類別中的建議`Shadows`假設如果都不`Shadows`也不`Overrides`指定<sup>2</sup>|`Overridable` 或`MustOverride`所需要的基底類別;`Overrides`衍生類別中所需|  
|繼承的類別衍生自您的衍生類別中重新定義項目|遮蔽項目繼承進一步衍生的類別;遮蔽的項目仍然隱藏<sup>3</sup>|覆寫項目繼承進一步衍生的類別;覆寫的元素，還是覆寫|  
  
 <sup>1</sup> *呼叫順序*項目類型所組成 (`Function`， `Sub`， `Operator`，或`Property`)、 名稱、 參數 清單中，並傳回型別。 您無法覆寫屬性或利用其他方式的程序。 您無法覆寫程序的一種 (`Function`， `Sub`，或`Operator`) 與另一種。  
  
 <sup>2</sup>如果您未指定其中一個`Shadows`或`Overrides`，編譯器會發出一則警告訊息可協助您確定要使用哪一種重複定義。 如果您忽略此警告，則會使用遮蔽的機制。  
  
 <sup>3</sup>進一步衍生類別中無法存取遮蔽項目時，無法繼承遮蔽。 例如，如果您宣告遮蔽的項目，做為`Private`，衍生自您的衍生類別繼承原始的項目，而非遮蔽的項目。  
  
## <a name="guidelines"></a>方針  
 您通常會使用覆寫在下列情況：  
  
-   您會定義多型的衍生的類別。  
  
-   您想讓編譯器強制的完全相同的項目類型和呼叫順序的安全。  
  
 您通常會使用下列案例中的遮蔽功能：  
  
-   您預期可能會修改基底類別，並定義為您使用相同名稱的項目。  
  
-   您想要能夠變更的項目類型，或呼叫順序。  
  
## <a name="see-also"></a>另請參閱

- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic 中的遮蔽功能](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [如何：隱藏與您的變數名稱相同的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [如何：隱藏繼承的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [如何：存取衍生類別所隱藏的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
