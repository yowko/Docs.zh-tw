---
title: Friend (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: 3e30267c8aa11ce97b3b3064ff0954378dab57af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959806"
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
指定一或多個宣告的程式設計項目, 只能從包含其宣告的元件中存取。  
  
## <a name="remarks"></a>備註  
 在許多情況下, 您會想要讓整個元件使用程式設計專案 (例如類別和結構), 而不只是宣告它們的元件。 不過, 您可能不想讓程式碼能夠透過元件外部的程式碼存取 (例如, 如果應用程式是專屬的)。 如果您想要以這種方式限制對專案的存取, 您可以使用`Friend`修飾詞來宣告該元素。  
  
 其他類別、結構和模組中編譯成相同元件的程式碼, 都可以存取該元件`Friend`中的所有元素。  
  
 `Friend`存取通常是應用程式設計項目的慣用層級, 而且`Friend`是介面、模組、類別或結構的預設存取層級。  
  
 您只能在`Friend`模組、介面或命名空間層級上使用。 因此, 專案的宣告內容`Friend`必須是原始程式檔、命名空間、介面、模組、類別或結構, 而不能是程式。  

> [!NOTE]
> 您也可以使用[受保護的 Friend](protected-friend.md)存取修飾詞, 讓類別成員可從類別內、衍生類別, 以及定義類別的相同元件中存取。 若要從相同元件中的類別和衍生類別限制成員的存取權, 您可以使用私用[保護](private-protected.md)的存取修飾詞。

 如需`Friend`和其他存取修飾詞的比較, 請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
> [!NOTE]
> 您可以指定另一個元件是 friend 元件, 讓它能夠存取所有標記為`Friend`的類型和成員。 如需詳細資訊，請參閱 [Friend Assemblies](../../../standard/assembly/friend-assemblies.md) (Friend 組件)。  
  
## <a name="example"></a>範例  
 下列類別會使用`Friend`修飾詞, 允許相同元件中的其他程式設計項目存取特定成員。  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a>使用量  
 您可以在這些`Friend`內容中使用修飾詞:  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
