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
# <a name="error-c-reference"></a><span data-ttu-id="e0303-102">#error (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e0303-102">#error (C# Reference)</span></span>

<span data-ttu-id="e0303-103">`#error` 可讓您從您程式碼中的特定位置產生 [CS1029](../compiler-messages/cs1029.md) 使用者定義錯誤。</span><span class="sxs-lookup"><span data-stu-id="e0303-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="e0303-104">例如：</span><span class="sxs-lookup"><span data-stu-id="e0303-104">For example:</span></span>

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> <span data-ttu-id="e0303-105">編譯器會 `#error version` 以特殊方式處理，並使用包含已使用之編譯器和語言版本的訊息來報告編譯器錯誤 CS8304。</span><span class="sxs-lookup"><span data-stu-id="e0303-105">The compiler treats `#error version` in a special way and reports a compiler error, CS8304, with a message containing the used compiler and language versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0303-106">備註</span><span class="sxs-lookup"><span data-stu-id="e0303-106">Remarks</span></span>

<span data-ttu-id="e0303-107">`#error` 常見於條件指示詞中。</span><span class="sxs-lookup"><span data-stu-id="e0303-107">A common use of `#error` is in a conditional directive.</span></span>

<span data-ttu-id="e0303-108">也可以使用 [#warning](./preprocessor-warning.md) 產生使用者定義警告。</span><span class="sxs-lookup"><span data-stu-id="e0303-108">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>

## <a name="example"></a><span data-ttu-id="e0303-109">範例</span><span class="sxs-lookup"><span data-stu-id="e0303-109">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e0303-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0303-110">See also</span></span>

- [<span data-ttu-id="e0303-111">C # 參考</span><span class="sxs-lookup"><span data-stu-id="e0303-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e0303-112">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e0303-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e0303-113">C # 預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="e0303-113">C# Preprocessor Directives</span></span>](./index.md)
