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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11f62b8fe8a28d6fe6401d53dac4b9bc1c45b21d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554593"
---
# <a name="instantiating-a-datetimeoffset-object"></a>具現化 DateTimeOffset 物件

<xref:System.DateTimeOffset>結構還提供數種方式來建立新<xref:System.DateTimeOffset>值。 其中有許多直接對應到可用來具現化新的方法<xref:System.DateTime>值，可讓您指定的日期和時間值的位移與 Coordinated Universal Time (UTC) 的增強功能。 特別是，您可以具現化<xref:System.DateTimeOffset>值如下：

* 使用日期和時間常值。

* 藉由呼叫<xref:System.DateTimeOffset>建構函式。

* 透過隱含地轉換到的值<xref:System.DateTimeOffset>值。

* 剖析日期和時間的字串表示。

本主題提供更詳細資料和程式碼範例，說明這些方法的具現化新<xref:System.DateTimeOffset>值。

## <a name="date-and-time-literals"></a>日期和時間常值

語言支援，其中一種最常見的方式來具現化<xref:System.DateTime>價值是提供的日期和時間做為硬式編碼的常值。 例如，下列 Visual Basic 程式碼會建立<xref:System.DateTime>物件，其值為 2008 年 1 月 1 日，上午 10:00。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> 值也可以初始化時使用支援的語言，使用日期和時間常值<xref:System.DateTime>常值。 例如，下列 Visual Basic 程式碼會建立<xref:System.DateTimeOffset>物件。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

如主控台輸出所示，<xref:System.DateTimeOffset>當地時區位移指派給以此方式建立的值。 這表示<xref:System.DateTimeOffset>指派使用字元常值不會識別單一時間點，如果在不同電腦上執行程式碼。

## <a name="datetimeoffset-constructors"></a>DateTimeOffset 建構函式

<xref:System.DateTimeOffset>型別定義了六個建構函式。 其中四個直接對應到<xref:System.DateTime>建構函式，使用額外的參數型別的<xref:System.TimeSpan>且定義日期和時間與 UTC 的位移。 這些可讓您定義<xref:System.DateTimeOffset>值根據其個別的日期和時間元件的值。 例如，下列程式碼會使用這些四個建構函式來具現化<xref:System.DateTimeOffset>物件具有相同的值時間 2008 年 7 月 1 日的上午 12:05 + 01:00。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

請注意，當的值<xref:System.DateTimeOffset>物件具現化使用<xref:System.Globalization.PersianCalendar>主控台就會顯示為其建構函式的引數的其中一個物件，它會表示為西曆，而不是與波斯曆中的日期。 若要輸出使用的波斯曆的日期，請參閱中的範例<xref:System.Globalization.PersianCalendar>主題。

其他兩個建構函式建立<xref:System.DateTimeOffset>物件從<xref:System.DateTime>值。 第一個具有單一參數，<xref:System.DateTime>要轉換成值<xref:System.DateTimeOffset>值。 產生的位移<xref:System.DateTimeOffset>值取決於<xref:System.DateTime.Kind%2A>建構函式的單一參數的屬性。 如果其值為<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>，則位移設定為等於<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。 否則，它的位移是設定為等於當地時區。 下列範例說明如何使用這個建構函式來具現化<xref:System.DateTimeOffset>代表 UTC 和當地時區物件：

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> 呼叫的多載<xref:System.DateTimeOffset>建構函式具有單一<xref:System.DateTime>參數相當於執行的隱含轉換<xref:System.DateTime>值<xref:System.DateTimeOffset>值。

建立第二個建構函式<xref:System.DateTimeOffset>物件從<xref:System.DateTime>值有兩個參數：<xref:System.DateTime>轉換值，和<xref:System.TimeSpan>代表的日期和時間的值與 UTC 的位移。 此位移的值必須對應到<xref:System.DateTime.Kind%2A>建構函式的第一個參數的屬性或<xref:System.ArgumentException>就會擲回。 如果<xref:System.DateTime.Kind%2A>屬性的第一個參數是<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>，第二個參數的值必須是<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。 如果<xref:System.DateTime.Kind%2A>屬性的第一個參數是<xref:System.DateTimeKind.Local?displayProperty=nameWithType>，第二個參數的值必須是本機系統的時區位移。 如果<xref:System.DateTime.Kind%2A>屬性的第一個參數是<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>，則位移可以是任何有效的值。 下列程式碼說明如何呼叫這個建構函式轉換<xref:System.DateTime>至<xref:System.DateTimeOffset>值。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>隱含類型轉換

<xref:System.DateTimeOffset>類型支援一個隱含類型轉換： 從<xref:System.DateTime>值<xref:System.DateTimeOffset>值。 隱含類型轉換是從某種類型到另一種類型的轉換，這不需要明確轉型 (在 C# 中) 或轉換 (在 Visual Basic 中)，而且不會遺失資訊。 這樣就可以使用如下所述的程式碼。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

產生的位移<xref:System.DateTimeOffset>值取決於<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性值。 如果其值為<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>，則位移設定為等於<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。 如果它的值為<xref:System.DateTimeKind.Local?displayProperty=nameWithType>或<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>，則位移設定為等於當地時區。

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>剖析日期和時間的字串表示

<xref:System.DateTimeOffset>類型支援四種方法可讓您和字串表示轉換的日期時間到<xref:System.DateTimeOffset>值：

* <xref:System.DateTimeOffset.Parse%2A>會嘗試將日期的字串表示轉換和時間<xref:System.DateTimeOffset>值，並擲回例外狀況，如果轉換失敗。

* <xref:System.DateTimeOffset.TryParse%2A>會嘗試將日期的字串表示轉換和時間<xref:System.DateTimeOffset>值，然後傳回`false`如果轉換失敗。

* <xref:System.DateTimeOffset.ParseExact%2A>會嘗試將日期和時間，以指定格式的字串表示轉換成<xref:System.DateTimeOffset>值。 方法會在轉換失敗時擲回例外狀況。

* <xref:System.DateTimeOffset.TryParseExact%2A>會嘗試將日期和時間，以指定格式的字串表示轉換成<xref:System.DateTimeOffset>值。 如果轉換失敗，方法會傳回 `false`。

下列範例說明對這些四個字串轉換方法呼叫，以具現化<xref:System.DateTimeOffset>值。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](../../../docs/standard/datetime/index.md)
