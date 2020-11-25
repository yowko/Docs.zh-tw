---
title: 重大變更： CA1831：針對字串使用 AsSpan 而非以範圍為基礎的索引子
description: 瞭解 .NET 5.0 中因為啟用程式碼分析規則 CA1831 所造成的重大變更。
ms.date: 08/21/2020
ms.openlocfilehash: 74f34af04a56b73478ffb3305d69ed49f3a30072
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760429"
---
# <a name="warning-ca1831-use-asspan-instead-of-range-based-indexers-for-string"></a>警告 CA1831：針對字串使用 AsSpan 而非以範圍為基礎的索引子

預設會啟用 .NET 程式碼分析器規則 [CA1831](/visualstudio/code-quality/ca1831) ，從 .net 5.0 開始。 它會產生任何程式碼的組建警告 <xref:System.Range> ，其中使用以字串為基礎的索引子，但未預期複製。

## <a name="change-description"></a>變更描述

從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../fundamentals/code-analysis/overview.md)。 預設會啟用這些規則中的數個，包括 [CA1831](/visualstudio/code-quality/ca1831)。 如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。

[規則 CA1831] 會尋找在 <xref:System.Range> 字串上使用以 a 為基礎之索引子的實例，但不會提供任何複本。 如果 <xref:System.Range> 以直接在字串上使用的索引子來產生隱含轉換，則會建立字串所要求部分的不必要複本。 例如：

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

CA1831 建議您 <xref:System.Range> 改為在字串 *範圍* 上使用以型索引子為基礎的索引子。 例如：

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

- 若要修正您的程式碼，並避免不必要的配置，請 <xref:System.MemoryExtensions.AsSpan(System.String)> <xref:System.MemoryExtensions.AsMemory(System.String)> 在使用 <xref:System.Range> 型索引子之前呼叫或。 例如：

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- 如果您不想變更您的程式碼，您可以將規則的嚴重性設定為或，以停用此規則 `suggestion` `none` 。 如需詳細資訊，請參閱 [設定程式碼分析規則](../../../../fundamentals/productivity/configure-code-analysis-rules.md)。

- 若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。 如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Range?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Range`

### Category

Code analysis

-->
