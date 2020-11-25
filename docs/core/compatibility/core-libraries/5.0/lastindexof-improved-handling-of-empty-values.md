---
title: 重大變更： LastIndexOf 已改善空白搜尋字串的處理
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中 LastIndexOf 和相關的 Api 在搜尋零長度的子字串時，現在會傳回正確的值。
ms.date: 11/01/2020
ms.openlocfilehash: 6d1a676eb2b9ed3de6a745db27d53bd43560a32f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760453"
---
# <a name="lastindexof-has-improved-handling-of-empty-search-strings"></a>LastIndexOf 已改善空白搜尋字串的處理

<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> 而相關的 Api 現在會在搜尋長度為零的 (或較大的字串中) 長度相等的子字串時，傳回正確的值。

## <a name="change-description"></a>變更描述

在 .NET Framework 和 .NET Core 1.0-3.1 中， <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> 當呼叫端搜尋零長度的子字串時，相關的 api 可能會傳回不正確的值。

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '4' (incorrect)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '0' (incorrect)
```

從 .NET 5.0 開始，這些 Api 會傳回的正確值 `LastIndexOf` 。

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '5' (correct)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '5' (correct)
```

在這些範例中， `5` 是正確的答案，因為 `"Hello".Substring(5)` 和 `"Hello".AsSpan().Slice(5)` 兩者都會產生空字串，其完整等於所搜尋的空白子字串。

## <a name="reason-for-change"></a>變更的原因

這項變更是在 .NET 5 的字串處理方面的整體 bug 修正工作的一部分。 它也可協助統一 Windows 與非 Windows 平臺之間的行為。 如需詳細資訊，請參閱 [dotnet/runtime # 13383](https://github.com/dotnet/runtime/issues/13383) 和 [dotnet/runtime # #13382](https://github.com/dotnet/runtime/issues/13382)。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

您不需要採取任何動作。 .NET 5.0 執行時間會自動提供新的行為。

沒有相容性參數可以還原舊行為。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.String.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.Globalization.CompareInfo.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.MemoryExtensions.LastIndexOf%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.String.LastIndexOf`
- `Overload:System.Globalization.CompareInfo.LastIndexOf`
- `Overload:System.MemoryExtensions.LastIndexOf`

-->
