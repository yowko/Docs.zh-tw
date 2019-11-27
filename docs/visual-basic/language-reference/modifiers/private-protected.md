---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 265141f77f4a61a61414a07214830feaa8a1ab05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351349"
---
# <a name="private-protected-visual-basic"></a>私用保護（Visual Basic）

`Private Protected` 關鍵字組合是成員存取修飾詞。 `Private Protected` 成員可由其包含類別中的所有成員，以及衍生自包含類別的類型來存取，但只有在其包含的元件中找到時，才會提供。

您只能在類別的成員上指定 `Private Protected`;您無法將 `Private Protected` 套用到結構的成員，因為無法繼承結構。

Visual Basic 15.5 和更新版本支援 `Private Protected` 存取修飾詞。 若要使用它，您可以將下列元素加入至 Visual Basic 專案（\*. vbproj）檔案。 只要您的系統上已安裝 Visual Basic 15.5 或更新版本，它就可讓您利用最新版本的 Visual Basic 編譯器所支援的所有語言功能：

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

如需詳細資訊，請參閱[設定 Visual Basic 語言版本](../../language-reference/configure-language-version.md)。

> [!NOTE]
> 在 Visual Studio 中，在 `private protected` 上選取 [F1 說明] 會提供[私](private.md)用或[受保護](protected.md)的協助。 IDE 會挑選游標下的單一 token，而不是複合字組。

## <a name="rules"></a>規則

- **宣告內容。** 您只能在類別層級使用 `Private Protected`。 這表示 `Protected` 元素的宣告內容必須是類別，而且不能是原始程式檔、命名空間、介面、模組、結構或程式。

## <a name="behavior"></a>行為

- **存取層級。** 類別中的所有程式碼都可以存取其元素。 任何衍生自基類且包含在相同元件中的類別中的程式碼，都可以存取基類的所有 `Private Protected` 元素。 不過，任何衍生自基類且包含在不同元件中的類別中的程式碼，都無法存取基底類別 `Private Protected` 元素。

- **存取修飾詞。** 指定存取層級的關鍵字稱為*存取*修飾詞。 如需存取修飾詞的比較，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。

`Private Protected` 修飾詞可用於以下內容：

- Nested 類別的[Class 語句](../../../visual-basic/language-reference/statements/class-statement.md)

- [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)

- [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)

- 在類別中嵌套之委派的[委派語句](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)

- 在類別中嵌套之列舉的[Enum 語句](../../../visual-basic/language-reference/statements/enum-statement.md)

- [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)

- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)

- 類別中所嵌套介面的[介面語句](../../../visual-basic/language-reference/statements/interface-statement.md)

- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)

- 類別中所嵌套結構的[結構語句](../../../visual-basic/language-reference/statements/structure-statement.md)

- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>另請參閱

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Protected Friend](./protected-friend.md)
- [Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
