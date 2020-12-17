---
title: 重大變更：還原序列化 char 需要單一字元字串
description: 瞭解 .NET 5.0 中的重大變更，在此情況下，System.Text.Json 在還原序列化至 char 目標時需要 JSON 中的單一字元字串。
ms.date: 12/15/2020
ms.openlocfilehash: 39a2d25b00bf8855cfbf46a4d78b8545052703e5
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633867"
---
# <a name="systemtextjson-requires-single-char-string-to-deserialize-a-char"></a>System.Text.Json 需要單一字元字串才能還原序列化字元

若要使用成功還原序列化 <xref:System.Char> <xref:System.Text.Json> ，JSON 字串必須包含單一字元。

## <a name="change-description"></a>變更描述

在先前的 .NET 版本中，JSON 中的多字串已成功還原序列化 `char` 為 `char` 屬性或欄位。 只 `char` 會使用第一個字串，如下列範例所示：

```csharp
// .NET Core 3.0 and 3.1: Returns the first char 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one char.
char deserializedChar = JsonSerializer.Deserialize<char>("\"abc\"");
```

在 .NET 5.0 和更新版本中，單一字串以外的任何其他作業都會導致在還原序列化 `char` <xref:System.Text.Json.JsonException> 目標為時擲回 `char` 。 下列範例字串已在所有 .NET 版本中成功還原序列化：

```csharp
// Correct usage.
char deserializedChar = JsonSerializer.Deserialize<char>("\"a\"");
```

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="reason-for-change"></a>變更的原因

只有當提供的裝載對目標型別有效時，才應該成功剖析還原序列化。 針對 `char` 類型，唯一有效的承載是單一 `char` 字串。

## <a name="recommended-action"></a>建議的動作

當您將 JSON 還原序列化為 `char` 目標時，請確定該字串包含單一 `char` 。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`

### Category

Serialization

-->
