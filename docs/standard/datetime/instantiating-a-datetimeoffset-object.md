---
title: 具現化 DateTimeOffset 物件
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
- DateTimeOffset structure, converting to DateTime
- DateTimeOffset structure, instantiating
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
ms.openlocfilehash: 1b1178623258393eab28a7087eb04c47b55a9176
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122317"
---
# <a name="instantiating-a-datetimeoffset-object"></a>具現化 DateTimeOffset 物件

<xref:System.DateTimeOffset> 結構提供數種方式來建立新的 <xref:System.DateTimeOffset> 值。 其中有許多是直接對應至可用來具現化新 <xref:System.DateTime> 值的方法，並提供增強功能，可讓您指定日期和時間值與國際標準時間（UTC）的位移。 特別的是，您可以透過下列方式將 <xref:System.DateTimeOffset> 值具現化：

- 使用日期和時間常值。

- 藉由呼叫 <xref:System.DateTimeOffset> 的函式。

- 藉由將值隱含地轉換為 <xref:System.DateTimeOffset> 值。

- 剖析日期和時間的字串表示。

本主題提供更多詳細資料和程式碼範例，說明將新的 <xref:System.DateTimeOffset> 值具現化的方法。

## <a name="date-and-time-literals"></a>日期和時間常值

針對支援的語言，將 <xref:System.DateTime> 值具現化的其中一個最常見方式，是以硬式編碼的常值形式提供日期和時間。 例如，下列 Visual Basic 程式碼會建立一個 <xref:System.DateTime> 物件，其值為2008年1月1日，上午10:00。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

使用支援 <xref:System.DateTime> 常值的語言時，也可以使用日期和時間常值來初始化 <xref:System.DateTimeOffset> 值。 例如，下列 Visual Basic 程式碼會建立 <xref:System.DateTimeOffset> 物件。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

如主控台輸出所示，以這種方式建立的 <xref:System.DateTimeOffset> 值會指派當地時區的時差。 這表示，如果程式碼是在不同的電腦上執行，則使用字元常值指派的 <xref:System.DateTimeOffset> 值不會識別單一時間點。

## <a name="datetimeoffset-constructors"></a>DateTimeOffset 構造函式

<xref:System.DateTimeOffset> 類型會定義六個函式。 其中四個直接對應至 <xref:System.DateTime> 的函式，並具有類型 <xref:System.TimeSpan> 的額外參數，可定義日期和時間與 UTC 之間的時差。 這些可讓您根據其個別日期和時間元件的值來定義 <xref:System.DateTimeOffset> 值。 例如，下列程式碼會使用這四個函式，將具有相同值 7/1/2008 12:05 AM + 01:00 的 <xref:System.DateTimeOffset> 物件具現化。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

請注意，當使用 <xref:System.Globalization.PersianCalendar> 物件來具現化 <xref:System.DateTimeOffset> 物件的值做為它的其中一個引數時，會顯示在主控台中，它會以西曆中的日期表示，而不是波斯曆。 若要使用波斯曆輸出日期，請參閱 <xref:System.Globalization.PersianCalendar> 主題中的範例。

其他兩個函數會從 <xref:System.DateTime> 值建立 <xref:System.DateTimeOffset> 物件。 其中的第一個參數只有一個參數，也就是要轉換成 <xref:System.DateTimeOffset> 值的 <xref:System.DateTime> 值。 產生之 <xref:System.DateTimeOffset> 值的位移取決於此函式的單一參數的 <xref:System.DateTime.Kind%2A> 屬性。 如果 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>其值，則會將位移設定為等於 <xref:System.TimeSpan.Zero?displayProperty=nameWithType>。 否則，它的位移是設定為等於當地時區。 下列範例說明如何使用此函式來具現化代表 UTC 和當地時區 <xref:System.DateTimeOffset> 物件：

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> 呼叫具有單一 <xref:System.DateTime> 參數的 <xref:System.DateTimeOffset> 函式的多載，相當於執行 <xref:System.DateTime> 值到 <xref:System.DateTimeOffset> 值的隱含轉換。

第二個從 <xref:System.DateTime> 值建立 <xref:System.DateTimeOffset> 物件的函式有兩個參數：要轉換的 <xref:System.DateTime> 值，以及代表日期和時間與 UTC 之位移的 <xref:System.TimeSpan> 值。 這個位移值必須對應至此函式第一個參數的 <xref:System.DateTime.Kind%2A> 屬性，否則會擲回 <xref:System.ArgumentException>。 如果第一個參數的 <xref:System.DateTime.Kind%2A> 屬性是 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>，則第二個參數的值必須是 <xref:System.TimeSpan.Zero?displayProperty=nameWithType>。 如果第一個參數的 <xref:System.DateTime.Kind%2A> 屬性是 <xref:System.DateTimeKind.Local?displayProperty=nameWithType>，則第二個參數的值必須是本機系統時區的位移。 如果第一個參數的 <xref:System.DateTime.Kind%2A> 屬性是 <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>，則位移可以是任何有效的值。 下列程式碼說明呼叫此函式，以將 <xref:System.DateTime> 轉換為 <xref:System.DateTimeOffset> 值。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>隱含類型轉換

<xref:System.DateTimeOffset> 類型支援一種隱含類型轉換：從 <xref:System.DateTime> 值到 <xref:System.DateTimeOffset> 值。 隱含類型轉換是從某種類型到另一種類型的轉換，這不需要明確轉型 (在 C# 中) 或轉換 (在 Visual Basic 中)，而且不會遺失資訊。 這樣就可以使用如下所述的程式碼。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

產生的 <xref:System.DateTimeOffset> 值的位移取決於 <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> 屬性值。 如果 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>其值，則會將位移設定為等於 <xref:System.TimeSpan.Zero?displayProperty=nameWithType>。 如果其值為 <xref:System.DateTimeKind.Local?displayProperty=nameWithType> 或 <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>，則位移會設定為等於當地時區的時差。

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>剖析日期和時間的字串標記法

<xref:System.DateTimeOffset> 類型支援四種方法，可讓您將日期和時間的字串表示轉換成 <xref:System.DateTimeOffset> 值：

- <xref:System.DateTimeOffset.Parse%2A>，它會嘗試將日期和時間的字串表示轉換為 <xref:System.DateTimeOffset> 值，並在轉換失敗時擲回例外狀況。

- <xref:System.DateTimeOffset.TryParse%2A>，它會嘗試將日期和時間的字串表示轉換為 <xref:System.DateTimeOffset> 值，並在轉換失敗時傳回 `false`。

- <xref:System.DateTimeOffset.ParseExact%2A>，它會嘗試將指定格式之日期和時間的字串表示轉換為 <xref:System.DateTimeOffset> 值。 方法會在轉換失敗時擲回例外狀況。

- <xref:System.DateTimeOffset.TryParseExact%2A>，它會嘗試將指定格式之日期和時間的字串表示轉換為 <xref:System.DateTimeOffset> 值。 如果轉換失敗，方法會傳回 `false`。

下列範例說明呼叫這四個字串轉換方法中的每一個，以具現化 <xref:System.DateTimeOffset> 值。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>請參閱

- [日期、時間及時區](../../../docs/standard/datetime/index.md)
