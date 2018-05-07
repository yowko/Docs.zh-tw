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
ms.openlocfilehash: a48ea87bb5eb1e302ae6a1169c22ea30bd4bc7ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="instantiating-a-datetimeoffset-object"></a>具現化 DateTimeOffset 物件

<xref:System.DateTimeOffset>結構提供數種方式來建立新<xref:System.DateTimeOffset>值。 其中許多直接對應到可用的方法具現化新<xref:System.DateTime>與增強功能，可讓您指定的日期和時間值國際標準時間 (UTC) 位移的值。 特別是，您可以具現化<xref:System.DateTimeOffset>值如下：

* 使用日期和時間常值。

* 藉由呼叫<xref:System.DateTimeOffset>建構函式。

* 透過隱含地將值轉換為<xref:System.DateTimeOffset>值。

* 剖析日期和時間的字串表示。

本主題提供更詳細資料和程式碼範例以說明這些方法具現化新<xref:System.DateTimeOffset>值。

## <a name="date-and-time-literals"></a>日期和時間常值

支援它，其中一種最常見的方式來具現化的語言<xref:System.DateTime>價值是提供的日期和時間做為硬式編碼的常值。 例如，下列 Visual Basic 程式碼會建立<xref:System.DateTime>物件，其值為 2008 年 1 月 1 日上午 10:00。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> 值也可以初始化使用支援的語言時，使用日期和時間常值<xref:System.DateTime>常值。 例如，下列 Visual Basic 程式碼會建立<xref:System.DateTimeOffset>物件。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

如主控台輸出所示，<xref:System.DateTimeOffset>以此方式建立的值會指派的當地時區位移。 這表示<xref:System.DateTimeOffset>使用字元常值指派的值無法識別單一時間點執行程式碼在不同電腦上。

## <a name="datetimeoffset-constructors"></a>DateTimeOffset 建構函式

<xref:System.DateTimeOffset>型別定義六個建構函式。 其中四個直接對應<xref:System.DateTime>的建構函式，其他的型別參數<xref:System.TimeSpan>所定義的日期和時間的 UTC 位移。 這些選項可讓您定義<xref:System.DateTimeOffset>值根據其個別的日期和時間元件的值。 例如，下列程式碼會使用這些四個建構函式來具現化<xref:System.DateTimeOffset>物件相同的值，2008 年 7 月 1 日的上午 12:05 + 01:00。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

請注意，當值<xref:System.DateTimeOffset>使用具現化物件<xref:System.Globalization.PersianCalendar>主控台就會顯示為其建構函式的引數的其中一個物件，表示為西曆，而不是波斯曆中的日期。 若要輸出使用波斯曆中的日期，請參閱中的範例<xref:System.Globalization.PersianCalendar>主題。

其他兩個建構函式建立<xref:System.DateTimeOffset>物件從<xref:System.DateTime>值。 第一個具有單一參數，<xref:System.DateTime>要轉換成值<xref:System.DateTimeOffset>值。 產生的位移<xref:System.DateTimeOffset>值取決於<xref:System.DateTime.Kind%2A>建構函式的單一參數的屬性。 如果其值為<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>，位移設為等於<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。 否則，它的位移是設定為等於當地時區。 下列範例說明如何使用這個建構函式來具現化<xref:System.DateTimeOffset>代表 UTC 與本地時區的物件：

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> 呼叫的多載<xref:System.DateTimeOffset>建構函式具有單一<xref:System.DateTime>參數相當於執行的隱含轉換<xref:System.DateTime>值設定為<xref:System.DateTimeOffset>值。

建立第二個建構函式<xref:System.DateTimeOffset>物件從<xref:System.DateTime>值有兩個參數：<xref:System.DateTime>轉換值，和<xref:System.TimeSpan>代表的日期和時間的值與 UTC 的時差。 此位移的值必須對應到<xref:System.DateTime.Kind%2A>建構函式的第一個參數的屬性或<xref:System.ArgumentException>就會擲回。 如果<xref:System.DateTime.Kind%2A>屬性的第一個參數是<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>，第二個參數的值必須是<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。 如果<xref:System.DateTime.Kind%2A>屬性的第一個參數是<xref:System.DateTimeKind.Local?displayProperty=nameWithType>，第二個參數的值必須是本機系統時區位移。 如果<xref:System.DateTime.Kind%2A>屬性的第一個參數是<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>，位移可以是任何有效的值。 下列程式碼說明如何呼叫這個建構函式轉換<xref:System.DateTime>至<xref:System.DateTimeOffset>值。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>隱含類型轉換

<xref:System.DateTimeOffset>類型支援一個隱含類型轉換： 從<xref:System.DateTime>值設定為<xref:System.DateTimeOffset>值。 隱含類型轉換是從某種類型到另一種類型的轉換，這不需要明確轉型 (在 C# 中) 或轉換 (在 Visual Basic 中)，而且不會遺失資訊。 這樣就可以使用如下所述的程式碼。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

產生的位移<xref:System.DateTimeOffset>值取決於<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性值。 如果其值為<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>，位移設為等於<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。 如果其值為 <xref:System.DateTimeKind.Local?displayProperty=nameWithType>或<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>，位移設為等於當地時區。

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>剖析日期和時間的字串的表示

<xref:System.DateTimeOffset>型別支援四種方法可讓您將日期的字串表示轉換成時間<xref:System.DateTimeOffset>值：

* <xref:System.DateTimeOffset.Parse%2A>它會嘗試轉換的字串表示日期和時間<xref:System.DateTimeOffset>值，並擲回例外狀況，如果轉換失敗。

* <xref:System.DateTimeOffset.TryParse%2A>它會嘗試轉換的字串表示日期和時間<xref:System.DateTimeOffset>值並傳回`false`如果轉換失敗。

* <xref:System.DateTimeOffset.ParseExact%2A>其中嘗試的日期和時間，以指定格式的字串表示轉換成<xref:System.DateTimeOffset>值。 方法會在轉換失敗時擲回例外狀況。

* <xref:System.DateTimeOffset.TryParseExact%2A>其中嘗試的日期和時間，以指定格式的字串表示轉換成<xref:System.DateTimeOffset>值。 如果轉換失敗，方法會傳回 `false`。

下列範例說明如何具現化每個四個字串轉換方法呼叫<xref:System.DateTimeOffset>值。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>另請參閱

[日期、時間和時區](../../../docs/standard/datetime/index.md)
