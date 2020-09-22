---
title: 公用
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: f2b6a126435b111ef56ee2a9870ea6fbddf87901
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867691"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)

指定一或多個宣告的程式設計項目沒有存取限制。  
  
## <a name="remarks"></a>備註  

 如果您要發行元件或元件集（例如類別庫），您通常會想要讓程式設計專案可供與您的元件互通的任何程式碼存取。 若要對專案授與這類無限制的存取權，您可以使用來宣告 `Public` 。  
  
 當您不需要限制對程式設計專案的存取權時，公用存取是程式設計項目的一般層級。 請注意，在介面、模組、類別或結構中宣告之專案的存取層級預設為， `Public` 否則為。  
  
## <a name="rules"></a>規則  
  
- **宣告內容。** 您 `Public` 只能在模組、介面或命名空間層級使用。 這表示元素的宣告內容 `Public` 必須是原始程式檔、命名空間、介面、模組、類別或結構，而且不能是程式。  
  
## <a name="behavior"></a>行為  
  
- **存取層級。** 所有可以存取模組、類別或結構的程式碼都可以存取其 `Public` 元素。  
  
- **預設存取。** 程式內的區域變數預設為公用存取，而且您不能在這些變數上使用任何存取修飾詞。  
  
- **存取修飾詞。** 指定存取層級的關鍵字稱為 *存取*修飾詞。 如需存取修飾詞的比較，請參閱 [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `Public` 修飾詞可用於以下內容：  
  
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
  
 [Operator Statement](../statements/operator-statement.md)  
  
 [Property Statement](../statements/property-statement.md)  
  
 [Structure 陳述式](../statements/structure-statement.md)  
  
 [Sub 陳述式](../statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [保護](protected.md)
- [Friend](friend.md)
- [私人](private.md)
- [私用保護](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)
- [程序](../../programming-guide/language-features/procedures/index.md)
- [結構](../../programming-guide/language-features/data-types/structures.md)
- [物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)
