---
title: 遮蔽和覆寫的差異
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: 98c073f8fa403416b2425431ff4334b990726f44
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095443"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>遮蔽和覆寫的差異 (Visual Basic)

當您定義繼承自基類的類別時，有時候您會想要重新定義衍生類別中的一個或多個基類元素。 遮蔽和覆寫都可用於此用途。  
  
## <a name="comparison"></a>比較  

 當衍生類別繼承自基類時，兩者都會使用遮蔽和覆寫，而且這兩個專案都是以另一個宣告的專案來重新定義。 但是兩者之間有顯著的差異。  
  
 下表比較遮蔽和覆寫。  
  
||||  
|---|---|---|  
|比較點|遮蔽|覆寫|  
|目的|防止後續的基類修改引進您已在衍生類別中定義的成員|藉由使用相同的呼叫順序<sup>1</sup>來定義程式或屬性的不同執行，以達到多型|  
|重新定義的元素|任何宣告的元素類型|只有 (`Function` 、 `Sub` 或 `Operator`) 或屬性的程式|  
|重新定義元素|任何宣告的元素類型|只有具有相同呼叫順序<sup>1</sup>的程式或屬性|  
|重新定義元素的存取層級|任何存取層級|無法變更覆寫元素的存取層級|  
|重新定義元素的可讀性和可寫性|任何組合|無法變更覆寫屬性的可讀性或可寫性|  
|控制重新定義|基類元素無法強制或禁止遮蔽|基類元素可以指定 `MustOverride` 、 `NotOverridable` 或 `Overridable`|  
|關鍵字使用方式|`Shadows` 建議使用於衍生類別; `Shadows` 如果未指定，則假設為 `Shadows` `Overrides` <sup>2</sup>|`Overridable` 或 `MustOverride` 基類中的必要項; `Overrides` 衍生類別中的必要項|  
|衍生自衍生類別之類別的重新定義元素繼承|其他衍生類別所繼承的遮蔽元素;隱藏的元素仍隱藏<sup>3</sup>|覆寫進一步衍生類別所繼承的元素;覆寫的元素仍被覆寫|  
  
 <sup>1</sup> *呼叫順序* 包含元素類型 (`Function` 、 `Sub` 、 `Operator` 或 `Property`) 、名稱、參數清單和傳回類型。 您無法以屬性或其他方式覆寫程式。 您無法使用另一種方法覆寫一種程式 (`Function` 、 `Sub` 或 `Operator`) 。  
  
 <sup>2</sup> 如果您未指定 `Shadows` 或 `Overrides` ，則編譯器會發出一則警告訊息，協助您確定要使用哪一種類型的重新定義。 如果您忽略此警告，則會使用遮蔽機制。  
  
 <sup>3</sup> 如果在其他衍生類別中無法存取遮蔽元素，則不會繼承遮蔽。 例如，如果您將遮蔽元素宣告為 `Private` ，則衍生自衍生類別的類別會繼承原始專案，而不是遮蔽元素。  
  
## <a name="guidelines"></a>指導方針  

 在下列情況下，您通常會使用覆寫：  
  
- 您正在定義多型衍生類別。  
  
- 您想要讓編譯器強制執行相同的專案類型和呼叫順序的安全。  
  
 在下列情況下，您通常會使用遮蔽：  
  
- 您預期您的基類可能會修改，並使用與您相同的名稱來定義專案。  
  
- 您想要自由變更元素類型或呼叫順序。  
  
## <a name="see-also"></a>另請參閱

- [References to Declared Elements](references-to-declared-elements.md)
- [Visual Basic 中的遮蔽功能](shadowing.md)
- [如何：隱藏與您的變數名稱相同的變數](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [如何：隱藏繼承的變數](how-to-hide-an-inherited-variable.md)
- [如何：存取衍生類別所隱藏的變數](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [覆寫](../../../language-reference/modifiers/overrides.md)
