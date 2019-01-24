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
ms.openlocfilehash: 9be3200300de308a70559536905d1e118a4a5fe4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616195"
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
指定一或多個宣告的程式設計元素，只能從包含其宣告的組件內加以存取。  
  
## <a name="remarks"></a>備註  
 在許多情況下，您想要的程式設計項目，例如類別和結構，以供整個組件中，不只是由其宣告的元件。 不過，您可能不想要存取組件外部的程式碼 （例如，如果應用程式專屬）。 如果您想要限制存取的項目，如此一來，您就可以將它宣告使用`Friend`修飾詞。  
  
 其他類別、 結構和編譯成相同的模組中的程式碼組件可以存取所有`Friend`該組件中的項目。  
  
 `Friend` 存取通常是慣用的應用程式的程式設計項目層級和`Friend`是預設存取層級的介面、 模組、 類別或結構。  
  
 您可以使用`Friend`只能在模組、 介面或命名空間層級。 因此，宣告內容`Friend`項目必須是原始程式檔、 命名空間、 介面、 模組、 類別或結構，不能在程序。  

> [!NOTE]
> 您也可以使用[Protected Friend](protected-friend.md)讓從該類別中，從衍生的類別，以及從相同的組件中定義類別中存取類別成員存取修飾詞。 若要限制存取的成員在其類別內，以及從衍生類別中相同的組件，您使用[Private Protected](private-protected.md)存取修飾詞。

 如需的比較`Friend`和其他存取修飾詞，請參閱 <<c2> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
> [!NOTE]
>  您可以指定另一個組件是 friend 組件，可讓它以存取所有類型和成員標記為`Friend`。 如需詳細資訊，請參閱 [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md) (Friend 組件)。  
  
## <a name="example"></a>範例  
 下列類別使用`Friend`修飾詞，以允許存取特定成員相同的組件中的其他程式設計項目。  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a>使用量  
 您可以使用`Friend`修飾詞，在這些內容中：  
  
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
- [在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
