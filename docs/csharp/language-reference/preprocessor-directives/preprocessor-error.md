---
title: '#error - C# 參考'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: cc1e0640886e3f3c1c74a54f64961a56c8b030e4
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812363"
---
# <a name="error-c-reference"></a>#error (C# 參考)

`#error` 可讓您從您程式碼中的特定位置產生 [CS1029](../compiler-messages/cs1029.md) 使用者定義錯誤。 例如：

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> 編譯器會 `#error version` 以特殊方式處理，並使用包含已使用之編譯器和語言版本的訊息來報告編譯器錯誤 CS8304。

## <a name="remarks"></a>備註

`#error` 常見於條件指示詞中。

也可以使用 [#warning](./preprocessor-warning.md) 產生使用者定義警告。

## <a name="example"></a>範例

```csharp
// preprocessor_error.cs
// CS1029 expected
#define DEBUG
class MainClass
{
    static void Main()
    {
#if DEBUG
#error DEBUG is defined
#endif
    }
}
```

## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 預處理器指示詞](./index.md)
