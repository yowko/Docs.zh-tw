---
title: 重大變更：非公用、無參數的函式未使用於還原序列化
description: 瞭解 .NET 5.0 中的重大變更，其中非公用、無參數的函式不再用於以 JsonSerializer 還原序列化。
ms.date: 10/18/2020
ms.openlocfilehash: 6bdcc92c61008aa4ee27370bbac4dbf4ee3ef7c8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760766"
---
# <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a>非公用、無參數的函式不會用於還原序列化

為了在所有支援的目標 framework 標記之間保持一致性 (Tfm) ，非公用的無參數函式預設不會再用於還原序列化 <xref:System.Text.Json.JsonSerializer> 。

## <a name="change-description"></a>變更描述

在支援 .NET Standard 2.0 和更新版本的 [ NuGet 套件上](https://www.nuget.org/packages/System.Text.Json/) 的獨立System.Text.Js（也就是 4.6.0 4.7.2 版本），其行為與 .net Core 3.0 和3.1 上的內建行為不一致。 在 .NET Core 3.x 上，內部和私用的函式可用於還原序列化。 在獨立封裝中，不允許非公用的函式，而且 <xref:System.MissingMethodException> 如果沒有定義任何公用的無參數的函式，就會擲回。

從 .NET 5.0 開始，nuget 套件5.0.0 上的 System.Text.Js，NuGet 套件和內建 Api 之間的行為是一致的。 依預設，序列化程式會忽略非公用的函式，包括無參數的函式。 序列化程式會使用下列其中一個用於還原序列化的函式：

- 使用批註的公用函式 <xref:System.Text.Json.Serialization.JsonConstructorAttribute> 。
- 公用無參數的函式。
- 公用參數化的函式 (是否為唯一的公用函式) 。

如果沒有這些可用的函式， <xref:System.NotSupportedException> 當您嘗試還原序列化類型時，就會擲回。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="reason-for-change"></a>變更的原因

- 若要在所有目標 framework 標記之間強制執行一致的行為 (可為 <xref:System.Text.Json?displayProperty=fullName> ( .Net Core 3.0 和更新版本的 tfm) ，以及 .NET Standard 2.0) 
- 因為 <xref:System.Text.Json.JsonSerializer> 不應該呼叫類型的非公用介面區，無論是函式、屬性或欄位。

## <a name="recommended-action"></a>建議的動作

- 如果您擁有類型且可行，請將無參數的函式設為公用。
- 否則，請 `JsonConverter<T>` 針對類型執行，並控制還原序列化行為。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

Serialization

-->
