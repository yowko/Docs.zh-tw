---
title: Protected (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: a80e504cc8e88dfc8968f70fee2c17991b28aff5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929462"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)
成員存取修飾詞，指定一或多個宣告的程式設計項目，只能從其本身的類別或衍生類別中存取。  
  
## <a name="remarks"></a>備註  
 有時候，在類別中宣告的程式設計專案包含敏感性資料或受限制的程式碼，而您想要限制對專案的存取。 不過，如果類別是可繼承的，而且您預期衍生類別的階層，則這些衍生類別可能需要存取資料或程式碼。 在這種情況下，您會想要從基類和所有衍生類別來存取元素。 若要以這種方式限制對專案的存取，您可以使用`Protected`來宣告該元素。  

> [!NOTE]
> `Protected`存取修飾詞可以與兩個其他修改者結合：
>
> - [受保護的 Friend](protected-friend.md)修飾詞可讓類別成員從該類別、衍生類別，以及定義類別的相同元件中存取。 
> - [私用保護](private-protected.md)的修飾詞可讓衍生類型存取類別成員，但只能在其包含的元件內使用。
  
## <a name="rules"></a>規則  
  
- **宣告內容。** 您只能在`Protected`類別層級使用。 這表示`Protected`元素的宣告內容必須是類別，而且不能是原始程式檔、命名空間、介面、模組、結構或程式。  

## <a name="behavior"></a>行為  
  
- **存取層級。** 類別中的所有程式碼都可以存取其元素。 任何衍生自基類的類別中的程式碼，都可以存取`Protected`基類的所有元素。 這適用于所有的衍生層代。 這表示，類別可以存取`Protected`基類基類的元素，依此類推。  
  
     受保護的存取不是 friend 存取的超集合或子集。  
  
- **存取修飾詞。** 指定存取層級的關鍵字稱為*存取*修飾詞。 如需存取修飾詞的比較，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `Protected` 修飾詞可用於以下內容：  
  
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
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
