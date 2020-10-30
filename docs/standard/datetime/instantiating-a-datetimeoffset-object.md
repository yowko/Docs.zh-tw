---
title: 具現化 DateTimeOffset 物件
description: 瞭解如何具現化 (在 .NET 中建立) DateTimeOffset 物件的實例。 深入瞭解日期 & 時間常值、函式、隱含類型轉換、& 更多資訊。
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET], instantiation
- DateTimeOffset structure, converting to DateTime
- DateTimeOffset structure, instantiating
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
ms.openlocfilehash: 4158a3d3bbd7ada87dd0c773cf9a0f5e001ad918
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063621"
---
# <a name="instantiating-a-datetimeoffset-object"></a>具現化 DateTimeOffset 物件

<xref:System.DateTimeOffset>結構提供數種方式來建立新的 <xref:System.DateTimeOffset> 值。 其中許多都直接對應至可用來具現化新 <xref:System.DateTime> 值的方法，並提供增強功能，可讓您指定日期和時間值與國際標準時間 (UTC) 之間的位移。 尤其是，您可以透過下列方式來具現化 <xref:System.DateTimeOffset> 值：

- 使用日期和時間常值。

- 藉由呼叫函式 <xref:System.DateTimeOffset> 。

- 藉由將值隱含轉換為 <xref:System.DateTimeOffset> 值。

- 剖析日期和時間的字串表示。

本主題提供更詳細的詳細資料和程式碼範例，說明將新值具現化的方法 <xref:System.DateTimeOffset> 。

## <a name="date-and-time-literals"></a>日期和時間常值

針對支援的語言，將值具現化的其中一個最常見方式 <xref:System.DateTime> 就是以硬式編碼的常值提供日期和時間。 例如，下列 Visual Basic 程式碼會建立一個 <xref:System.DateTime> 物件，其值為2008年1月1日上午10:00 點。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> 使用支援常值的語言時，也可以使用日期和時間常值來初始化值 <xref:System.DateTime> 。 例如，下列 Visual Basic 程式碼會建立 <xref:System.DateTimeOffset> 物件。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

當主控台輸出顯示時， <xref:System.DateTimeOffset> 以這種方式建立的值會被指派本地時區的位移。 這表示， <xref:System.DateTimeOffset> 如果程式碼是在不同的電腦上執行，則使用字元常值指派的值不會識別單一時間點。

## <a name="datetimeoffset-constructors"></a>DateTimeOffset 函數

此 <xref:System.DateTimeOffset> 類型會定義六個函式。 其中四個會直接對應至函 <xref:System.DateTime> 式，其中有一個類型的額外參數， <xref:System.TimeSpan> 可定義日期和時間與 UTC 之間的時差。 這些可讓您 <xref:System.DateTimeOffset> 根據其個別日期和時間元件的值來定義值。 例如，下列程式碼會使用這四個函式來具現化 <xref:System.DateTimeOffset> 相同 7/1/2008 12:05 AM + 01:00 值的物件。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

請注意，當 <xref:System.DateTimeOffset> 使用物件具現化的物件值 <xref:System.Globalization.PersianCalendar> 做為其函式的其中一個引數時，會顯示在主控台中，它是以西曆中的日期來表示，而不是以波斯曆表示。 若要使用波斯曆輸出日期，請參閱主題中的範例 <xref:System.Globalization.PersianCalendar> 。

其他兩個函數會 <xref:System.DateTimeOffset> 從值建立物件 <xref:System.DateTime> 。 其中第一個參數有單一參數，也就是 <xref:System.DateTime> 要轉換成值的值 <xref:System.DateTimeOffset> 。 結果值的位移 <xref:System.DateTimeOffset> 取決於函式的 <xref:System.DateTime.Kind%2A> 單一參數的屬性。 如果其值為 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ，則會將位移設定為等於 <xref:System.TimeSpan.Zero?displayProperty=nameWithType> 。 否則，它的位移是設定為等於當地時區。 下列範例說明如何使用這個函式來具現化 <xref:System.DateTimeOffset> 代表 UTC 和本地時區的物件：

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> 呼叫具有單一參數之函式的多載， <xref:System.DateTimeOffset> <xref:System.DateTime> 相當於執行值的隱含轉換 <xref:System.DateTime> <xref:System.DateTimeOffset> 。

從值建立物件的第二個函式 <xref:System.DateTimeOffset> <xref:System.DateTime> 有兩個參數： <xref:System.DateTime> 要轉換的值，以及 <xref:System.TimeSpan> 代表日期和時間與 UTC 之間的位移的值。 此位移值必須對應至函 <xref:System.DateTime.Kind%2A> 式之第一個參數的屬性，否則 <xref:System.ArgumentException> 會擲回。 如果 <xref:System.DateTime.Kind%2A> 第一個參數的屬性是 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ，則第二個參數的值必須是 <xref:System.TimeSpan.Zero?displayProperty=nameWithType> 。 如果 <xref:System.DateTime.Kind%2A> 第一個參數的屬性是 <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ，則第二個參數的值必須是本機系統時區的位移。 如果 <xref:System.DateTime.Kind%2A> 第一個參數的屬性是 <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> ，則位移可以是任何有效的值。 下列程式碼說明如何呼叫這個函式以轉換 <xref:System.DateTime> 成 <xref:System.DateTimeOffset> 值。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>隱含類型轉換

此 <xref:System.DateTimeOffset> 類型支援一種隱含類型轉換：從 <xref:System.DateTime> 值到 <xref:System.DateTimeOffset> 值。 隱含類型轉換是從某種類型到另一種類型的轉換，這不需要明確轉型 (在 C# 中) 或轉換 (在 Visual Basic 中)，而且不會遺失資訊。 這樣就可以使用如下所述的程式碼。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

結果值的位移 <xref:System.DateTimeOffset> 取決於 <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> 屬性值。 如果其值為 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ，則會將位移設定為等於 <xref:System.TimeSpan.Zero?displayProperty=nameWithType> 。 如果其值為 <xref:System.DateTimeKind.Local?displayProperty=nameWithType> 或 <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> ，則位移的設定等於本地時區的值。

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>剖析日期和時間的字串表示

此 <xref:System.DateTimeOffset> 類型支援四種方法，可讓您將日期和時間的字串表示轉換成 <xref:System.DateTimeOffset> 值：

- <xref:System.DateTimeOffset.Parse%2A>，它會嘗試將日期和時間的字串表示轉換成 <xref:System.DateTimeOffset> 值，如果轉換失敗，則會擲回例外狀況。

- <xref:System.DateTimeOffset.TryParse%2A>，它會嘗試將日期和時間的字串表示轉換成 <xref:System.DateTimeOffset> 值，並 `false` 在轉換失敗時傳回。

- <xref:System.DateTimeOffset.ParseExact%2A>，它會嘗試將日期和時間的字串表示轉換成 <xref:System.DateTimeOffset> 值。 方法會在轉換失敗時擲回例外狀況。

- <xref:System.DateTimeOffset.TryParseExact%2A>，它會嘗試將日期和時間的字串表示轉換成 <xref:System.DateTimeOffset> 值。 如果轉換失敗，方法會傳回 `false`。

下列範例說明如何呼叫這四個字串轉換方法，以具現化 <xref:System.DateTimeOffset> 值。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](index.md)
