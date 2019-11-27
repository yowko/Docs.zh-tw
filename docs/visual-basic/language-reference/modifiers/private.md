---
title: 私人
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 5600744aeca79a54f51a1f9ecd0ef00fed4b00fd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351337"
---
# <a name="private-visual-basic"></a>Private (Visual Basic)
指定一或多個宣告的程式設計項目，只能從其宣告內容中存取，包括從任何包含的類型內。  
  
## <a name="remarks"></a>備註  
 如果程式設計項目代表專屬功能，或包含機密資料，您通常會想要盡可能嚴格地限制其存取。 您只允許定義它的模組、類別或結構來存取它，藉以達到最大限制。 若要以這種方式限制對專案的存取，您可以使用 `Private`來宣告該元素。  

> [!NOTE]
> 您也可以使用[私用保護](private-protected.md)的存取修飾詞，讓成員可以從該類別內，以及從位於其包含元件中的衍生類別中存取。

## <a name="rules"></a>規則  

- **宣告內容。** 您只能在模組層級使用 `Private`。 這表示 `Private` 元素的宣告內容必須是模組、類別或結構，而且不能是原始程式檔、命名空間、介面或程式。  
  
## <a name="behavior"></a>行為  
  
- **存取層級。** 宣告內容中的所有程式碼都可以存取其 `Private` 元素。 這包括包含類型內的程式碼，例如列舉中的嵌套類別或指派運算式。 宣告內容以外的程式碼都不能存取其 `Private` 元素。  
  
- **存取修飾詞。** 指定存取層級的關鍵字稱為*存取*修飾詞。 如需存取修飾詞的比較，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `Private` 修飾詞可用於以下內容：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private Protected](./private-protected.md)
- Visual Basic 中[受保護的 Friend](./protected-friend.md)[存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
