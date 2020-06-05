---
title: Protected Friend
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 202d4f4a3a05a64ab1d74621268f28f6b55e8952
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404832"
---
# <a name="protected-friend-visual-basic"></a>受保護的 Friend （Visual Basic）

`Protected Friend` 關鍵字組合是成員存取修飾詞。 它會在宣告的元素上授[Friend](friend.md)存取和[受保護](protected.md)的存取，因此可以從相同元件中的任何位置、從其本身的類別，以及從衍生類別存取。 您 `Protected Friend` 只能在類別的成員上指定，因為無法繼承結構，所以無法套用 `Protected Friend` 到結構的成員。

> [!NOTE]
> 在 Visual Studio 中，選取 [F1 `protected friend` 說明] 會提供[受保護](protected.md)或[friend](friend.md)的協助。 IDE 會挑選游標下的單一 token，而不是複合字組。

## <a name="rules"></a>規則

**宣告內容。** 您 `Protected Friend` 只能在類別層級使用。 這表示元素的宣告內容 `Protected` 必須是類別，而且不能是原始程式檔、命名空間、介面、模組、結構或程式。

## <a name="see-also"></a>另請參閱

- [公開](public.md)
- [免受](protected.md)
- [給](friend.md)
- [私用](private.md)
- [私用保護](./private-protected.md)
- [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)
- [程序](../../programming-guide/language-features/procedures/index.md)
- [結構](../../programming-guide/language-features/data-types/structures.md)
- [物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)
