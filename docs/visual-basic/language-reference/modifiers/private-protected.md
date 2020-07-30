---
title: Private Protected
ms.date: 05/10/2018
f1_keywords:
- vb.PrivateProtected
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 8ad1509da71bc80b33700d363ddd4569a0965dff
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303461"
---
# <a name="private-protected-visual-basic"></a>私用保護（Visual Basic）

`Private Protected` 關鍵字組合是成員存取修飾詞。 `Private Protected`成員可由其包含類別中的所有成員，以及衍生自包含類別的類型來存取，但只有在其包含的元件中找到時才可以。

您 `Private Protected` 只能在類別的成員上指定，因為無法繼承結構，所以無法套用 `Private Protected` 到結構的成員。

`Private Protected`Visual Basic 15.5 和更新版本支援存取修飾詞。 若要使用它，您可以將下列元素加入至 Visual Basic 專案（ \* . vbproj）檔案。 只要您的系統上已安裝 Visual Basic 15.5 或更新版本，它就可讓您利用最新版本的 Visual Basic 編譯器所支援的所有語言功能：

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

如需詳細資訊，請參閱[設定 Visual Basic 語言版本](../configure-language-version.md)。

> [!NOTE]
> 在 Visual Studio 中，選取 [F1 `private protected` 說明] 會提供[私](private.md)用[或受保護](protected.md)的協助。 IDE 會挑選游標下的單一 token，而不是複合字組。

## <a name="rules"></a>規則

- **宣告內容。** 您 `Private Protected` 只能在類別層級使用。 這表示元素的宣告內容 `Protected` 必須是類別，而且不能是原始程式檔、命名空間、介面、模組、結構或程式。

## <a name="behavior"></a>行為

- **存取層級。** 類別中的所有程式碼都可以存取其元素。 任何衍生自基類且包含在相同元件中的類別中的程式碼，都可以存取基類的所有 `Private Protected` 元素。 不過，任何衍生自基類且包含在不同元件中的類別中的程式碼，都無法存取基類 `Private Protected` 元素。

- **存取修飾詞。** 指定存取層級的關鍵字稱為*存取*修飾詞。 如需存取修飾詞的比較，請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。

`Private Protected` 修飾詞可用於以下內容：

- Nested 類別的[Class 語句](../statements/class-statement.md)

- [Const 陳述式](../statements/const-statement.md)

- [Declare Statement](../statements/declare-statement.md)

- 在類別中嵌套之委派的[委派語句](../statements/delegate-statement.md)

- [Dim 陳述式](../statements/dim-statement.md)

- 在類別中嵌套之列舉的[Enum 語句](../statements/enum-statement.md)

- [Event 陳述式](../statements/event-statement.md)

- [Function 陳述式](../statements/function-statement.md)

- 類別中所嵌套介面的[介面語句](../statements/interface-statement.md)

- [Property Statement](../statements/property-statement.md)

- 類別中所嵌套結構的[結構語句](../statements/structure-statement.md)

- [Sub 陳述式](../statements/sub-statement.md)

## <a name="see-also"></a>另請參閱

- [公開](public.md)
- [免受](protected.md)
- [給](friend.md)
- [私用](private.md)
- [Protected Friend](./protected-friend.md)
- [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)
- [程序](../../programming-guide/language-features/procedures/index.md)
- [結構](../../programming-guide/language-features/data-types/structures.md)
- [物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)
