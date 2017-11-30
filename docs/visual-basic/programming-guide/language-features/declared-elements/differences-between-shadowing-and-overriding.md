---
title: "遮蔽和覆寫的差異 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d67486d9c6af96d314abad7142ba86779d74f5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>遮蔽和覆寫的差異 (Visual Basic)
當您定義類別繼承自基底類別時，您有時會想要重新定義一或多個衍生類別中的基底類別項目。 遮蔽和覆寫都可供此目的。  
  
## <a name="comparison"></a>比較  
 遮蔽和覆寫同時使用當在衍生的類別繼承自基底類別，並同時重新定義與另一個宣告的項目。 但有兩個重大差異。  
  
 下表比較遮蔽和覆寫。  
  
||||  
|---|---|---|  
|比較點|遮蔽|覆寫|  
|用途|防止後續的基底類別修改引入您已定義在衍生類別中的成員|藉由定義不同的實作程序或屬性具有相同的呼叫順序達成多型<sup>1</sup>|  
|已重新定義的項目|任何宣告項目類型|程序 (`Function`， `Sub`，或`Operator`) 或屬性|  
|重新定義項目|任何宣告項目類型|只有程序或屬性具有相同的呼叫順序<sup>1</sup>|  
|存取層級的重新定義項目|任何存取層級|無法變更存取層級覆寫的元素|  
|閱讀，並重新定義項目的可寫性|任何組合|無法變更可讀性或可寫性的覆寫屬性|  
|重新定義的控制|無法在強制執行或禁止遮蔽基底類別項目|可以指定基底類別項目`MustOverride`， `NotOverridable`，或`Overridable`|  
|關鍵字的使用方式|`Shadows`衍生類別中的建議`Shadows`假設如果兩者皆非`Shadows`也`Overrides`指定<sup>2</sup>|`Overridable`或`MustOverride`所需要的基底類別; 事件類別`Overrides`衍生類別中所需|  
|繼承的類別衍生自您的衍生類別重新定義項目|遮蔽項目繼承進一步衍生的類別。遮蔽的項目仍然隱藏<sup>3</sup>|覆寫項目所繼承的進一步衍生的類別。覆寫的元素，還是覆寫|  
  
 <sup>1</sup> *呼叫順序*組成的項目類型 (`Function`， `Sub`， `Operator`，或`Property`)、 名稱、 參數清單和傳回型別。 您無法覆寫屬性或利用其他方式的程序。 您無法覆寫程序的一種 (`Function`， `Sub`，或`Operator`) 與另一種。  
  
 <sup>2</sup>如果您未指定`Shadows`或`Overrides`，編譯器會發出警告訊息，以協助您務必要使用哪種重複定義。 如果您忽略此警告，則會使用遮蔽的機制。  
  
 <sup>3</sup>進一步衍生類別中無法存取遮蔽項目是否不繼承遮蔽。 例如，如果您宣告遮蔽的項目，做為`Private`，從您的衍生類別中衍生的類別會繼承原始項目，而不是遮蔽的項目。  
  
## <a name="guidelines"></a>方針  
 您通常用在下列情況下覆寫：  
  
-   您正在定義多型的衍生的類別。  
  
-   您想讓編譯器強制執行相同的項目類型和呼叫順序的安全性。  
  
 您通常用在下列情況中的遮蔽功能：  
  
-   您預期基底類別可能會被修改，並定義為您使用相同名稱的項目。  
  
-   您想要變更的項目類型，或呼叫順序自由。  
  
## <a name="see-also"></a>另請參閱  
 [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic 中的遮蔽功能](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [如何：隱藏與您的變數名稱相同的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [如何：隱藏繼承的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [如何：存取衍生類別所隱藏的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
