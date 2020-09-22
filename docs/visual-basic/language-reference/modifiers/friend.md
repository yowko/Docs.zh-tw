---
title: Friend
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
ms.openlocfilehash: d37a93343822d069295477958780c2b9c72043fa
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875455"
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)

指定一或多個宣告的程式設計專案只能從包含其宣告的元件內進行存取。  
  
## <a name="remarks"></a>備註  

 在許多情況下，您會想要讓整個元件使用程式設計專案（例如類別和結構），而不只是由宣告它們的元件使用。 不過，您可能不想讓元件之外的程式碼能夠存取它們 (例如，如果應用程式是專屬的) 。 如果您想要以這種方式限制對專案的存取，可以使用修飾詞來宣告 `Friend` 。  
  
 其他類別、結構以及編譯成相同元件的模組中的程式碼，都可以存取 `Friend` 該元件中的所有元素。  
  
 `Friend` 存取通常是應用程式程式設計項目的慣用層級，而且 `Friend` 是介面、模組、類別或結構的預設存取層級。  
  
 您 `Friend` 只能在模組、介面或命名空間層級使用。 因此，元素的宣告內容 `Friend` 必須是原始程式檔、命名空間、介面、模組、類別或結構，但不能是程式。  

> [!NOTE]
> 您也可以使用 [受保護的 Friend](protected-friend.md) 存取修飾詞，讓類別成員可以從該類別、衍生類別，以及定義類別的相同元件中存取。 若要在其類別中以及從相同元件中的衍生類別，限制成員的存取權，您可以使用 [私用受保護](private-protected.md) 的存取修飾詞。

 如需和其他存取修飾詞的比較 `Friend` ，請參閱 [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。  
  
> [!NOTE]
> 您可以指定另一個元件是 friend 元件，讓它能夠存取標記為的所有類型和成員 `Friend` 。 如需詳細資訊，請參閱 [Friend 元件](../../../standard/assembly/friend.md)。

## <a name="example"></a>範例  

 下列類別會使用 `Friend` 修飾詞，以允許相同元件中的其他程式設計專案存取某些成員。  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a>使用方式  

 您可以 `Friend` 在這些內容中使用修飾詞：  
  
 [Class 陳述式](../statements/class-statement.md)  
  
 [Const 陳述式](../statements/const-statement.md)  
  
 [Declare Statement](../statements/declare-statement.md)  
  
 [Delegate 陳述式](../statements/delegate-statement.md)  
  
 [Dim 陳述式](../statements/dim-statement.md)  
  
 [End 陳述式](../statements/enum-statement.md)  
  
 [Event 陳述式](../statements/event-statement.md)  
  
 [Function 陳述式](../statements/function-statement.md)  
  
 [Interface 陳述式](../statements/interface-statement.md)  
  
 [Module 陳述式](../statements/module-statement.md)  
  
 [Property Statement](../statements/property-statement.md)  
  
 [Structure 陳述式](../statements/structure-statement.md)  
  
 [Sub 陳述式](../statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [公開](public.md)
- [保護](protected.md)
- [私人](private.md)
- [私用保護](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)
- [程序](../../programming-guide/language-features/procedures/index.md)
- [結構](../../programming-guide/language-features/data-types/structures.md)
- [物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)
