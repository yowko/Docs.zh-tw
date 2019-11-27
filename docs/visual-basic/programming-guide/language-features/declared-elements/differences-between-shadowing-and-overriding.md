---
title: 遮蔽和覆寫的差異
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: 8d1ebdcd0a23dff69a7acca22268c03e30ec06d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345422"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>遮蔽和覆寫的差異 (Visual Basic)
當您定義繼承自基類的類別時，您有時會想要重新定義衍生類別中的一個或多個基類元素。 遮蔽和覆寫皆可用於此用途。  
  
## <a name="comparison"></a>比較  
 當衍生類別繼承基類時，會使用遮蔽和覆寫，而這兩個專案都是以另一個宣告的專案重新定義。 但是兩者之間有顯著的差異。  
  
 下表會比較與覆寫的遮蔽。  
  
||||  
|---|---|---|  
|比較點|遮蔽|覆寫|  
|目的|防止後續的基類修改，引進您已在衍生類別中定義的成員。|藉由定義具有相同呼叫順序<sup>1</sup>的程式或屬性的不同執行，來達到多型|  
|已重新定義元素|任何宣告的元素類型|只有程式（`Function`、`Sub`或 `Operator`）或屬性|  
|重新定義元素|任何宣告的元素類型|只有具有相同呼叫順序<sup>1</sup>的程式或屬性|  
|重新定義元素的存取層級|任何存取層級|無法變更覆寫元素的存取層級|  
|重新定義元素的可讀性和可寫性|任何組合|無法變更覆寫屬性的可讀性或可寫性|  
|控制重新定義|基類元素無法強制或禁止遮蔽|基類元素可以指定 `MustOverride`、`NotOverridable`或 `Overridable`|  
|關鍵字使用方式|建議在衍生類別中 `Shadows`;`Shadows` 假設 `Shadows` 或 `Overrides` 都未指定<sup>2</sup>|在基類中需要 `Overridable` 或 `MustOverride`;衍生類別中需要 `Overrides`|  
|繼承自衍生類別之類別的重新定義元素|其他衍生類別所繼承的遮蔽元素;陰影元素仍然隱藏<sup>3</sup>|覆寫由進一步衍生類別繼承的元素;覆寫的元素仍然被覆寫|  
  
 <sup>1</sup> *呼叫序列*是由元素類型（`Function`、`Sub`、`Operator`或 `Property`）、名稱、參數清單和傳回類型所組成。 您不能使用屬性來覆寫程式，也無法以另一種方式來覆寫。 您不能以另一種方法覆寫一種程式（`Function`、`Sub`或 `Operator`）。  
  
 <sup>2</sup>如果您未指定 `Shadows` 或 `Overrides`，則編譯器會發出警告訊息，協助您確定要使用哪種重新定義。 如果您忽略此警告，則會使用遮蔽機制。  
  
 <sup>3</sup>如果在進一步的衍生類別中無法存取遮蔽元素，則不會繼承遮蔽。 例如，如果您將遮蔽專案宣告為 `Private`，衍生自衍生類別的類別會繼承原始專案，而不是遮蔽元素。  
  
## <a name="guidelines"></a>方針  
 在下列情況下，您通常會使用覆寫：  
  
- 您正在定義多型的衍生類別。  
  
- 您想要讓編譯器強制執行完全相同的元素類型和呼叫順序的安全性。  
  
 在下列情況下，您通常會使用遮蔽：  
  
- 您預期您的基類可能已修改，並使用與您相同的名稱來定義元素。  
  
- 您想要能夠自由變更元素類型或呼叫順序。  
  
## <a name="see-also"></a>請參閱

- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic 中的陰影](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [如何：隱藏與您的變數名稱相同的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [如何：隱藏繼承的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [如何：存取衍生類別所隱藏的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
