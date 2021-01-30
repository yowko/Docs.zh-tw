---
description: '##pragma warning - C# 參考'
title: '##pragma warning - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 16582a74bd34f2c0d89950280f1d5fde25435eea
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215988"
---
# <a name="pragma-warning-c-reference"></a>#pragma warning (C# 參考)

`#pragma warning` 可以啟用或停用特定警告。

## <a name="syntax"></a>語法

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

## <a name="parameters"></a>參數

 `warning-list` 以逗號分隔的警告編號清單。 "CS" 前置詞是選擇性的。

 未指定警告編號時，`disable` 會停用所有警告，而 `restore` 會啟用所有警告。

> [!NOTE]
> 若要尋找 Visual Studio 中的警告編號，請建立專案，然後在 [輸出] 視窗中尋找警告編號。

## <a name="example"></a>範例

```csharp
// pragma_warning.cs
using System;

#pragma warning disable 414, CS3021
[CLSCompliant(false)]
public class C
{
    int i = 1;
    static void Main()
    {
    }
}
#pragma warning restore CS3021
[CLSCompliant(false)]  // CS3021
public class D
{
    int i = 1;
    public static void F()
    {
    }
}
```

## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 預處理器指示詞](./index.md)
- [C # 編譯器錯誤](../compiler-messages/index.md)
- [如何隱藏程式碼分析警告](../../../fundamentals/code-analysis/suppress-warnings.md)
