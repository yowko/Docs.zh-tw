---
title: "'<expression>' 不能當做類型條件約束使用"
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: ff51bb27847a92b07ce6275a8ddee4789e865f08
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642808"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a>'\<運算式 >' 無法當做類型條件約束
條件約束清單包含運算式，此運算式不表示類型參數上有效的條件約束。  
  
 條件約束清單會對傳遞至類型參數的類型引數強制一些必要需求。 您可以利用任意組合指定下列需求：  
  
- 類型引數必須實作一或多個介面  
  
- 類型引數最多只能繼承自一個類別  
  
- 類型引數必須公開建立程式碼可以存取的無參數建構函式 (包含 `New` 條件約束)  
  
 如果您未在條件約束清單中包含任何特定類別或介面，則可以指定下列其中一項以強制更一般的需求：  
  
- 類型引數必須是實值類型 (包含 `Structure` 條件約束)  
  
- 類型引數必須是參考類型 (包含 `Class` 條件約束)  
  
 您無法針對相同的類型參數同時指定 `Structure` 和 `Class` ，並且無法多次指定其中一個。  
  
 **錯誤 ID:** BC32061  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 驗證是否有正確拼寫運算式與它的項目。  
  
- 如果運算式不符合上述的需求清單，請將它從條件約束清單中移除。  
  
- 如果運算式參考介面或類別，請驗證編譯器是否有權存取該介面或類別。 您可能需要限定其名稱，而且也可能需要將參考加入專案中。 如需詳細資訊，請參閱 < 專案參考 」 中[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
## <a name="see-also"></a>另請參閱

- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Value Types and Reference Types](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
