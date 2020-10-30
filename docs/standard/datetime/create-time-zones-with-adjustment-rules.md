---
title: 作法：建立有調整規則的時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], creating
- time zones [.NET], and adjustment rules
- adjustment rule [.NET]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
ms.openlocfilehash: 28ab7c8ceabcfd64a6797cf5a85869c469963983
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063816"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>作法：建立有調整規則的時區

應用程式所需的精確時區資訊可能不會出現在特定的系統上，有許多原因：

- 本機系統的登錄中從未定義過時區。

- 已從登錄中修改或移除有關時區的資料。

- 時區沒有特定歷程記錄期間時區調整的精確資訊。

在這些情況下，您可以呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法來定義應用程式所需的時區。 您可以使用這個方法的多載，建立具有或不含調整規則的時區。 如果時區支援日光節約時間，您可以使用固定或浮動調整規則來定義調整。  (如需這些詞彙的定義，請參閱 [時區總覽](time-zone-overview.md)中的「時區術語」一節。 ) 

> [!IMPORTANT]
> 藉由呼叫方法建立的自訂時區， <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 不會新增至登錄中。 相反地，只能透過方法呼叫所傳回的物件參考來存取它們 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 。

本主題顯示如何建立具有調整規則的時區。 若要建立不支援日光節約時間調整規則的時區，請參閱 [如何：建立沒有調整規則的時區](create-time-zones-without-adjustment-rules.md)。

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>建立具有浮動調整規則的時區

1. 針對每個調整 (也就是每個轉換在特定時間間隔) 的來回轉換，請執行下列動作：

    1. 定義時區調整的開始轉換時間。

       您必須呼叫 <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> 方法，並傳遞一個 <xref:System.DateTime> 值來定義轉換的時間、定義轉換之月份的整數值、定義發生轉換之周的整數值，以及 <xref:System.DayOfWeek> 定義發生轉換之周間日期的值，。 這個方法呼叫會具現化 <xref:System.TimeZoneInfo.TransitionTime> 物件。

    2. 定義時區調整的結束轉換時間。 這需要對方法進行另一次呼叫 <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> 。 這個方法呼叫會具現化第二個 <xref:System.TimeZoneInfo.TransitionTime> 物件。

    3. 呼叫 <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> 方法，並將調整的有效開始日期和結束日期、 <xref:System.TimeSpan> 定義轉換中的時間量的物件，以及 <xref:System.TimeZoneInfo.TransitionTime> 定義從日光節約時間轉換的兩個物件傳遞給它。 這個方法呼叫會具現化 <xref:System.TimeZoneInfo.AdjustmentRule> 物件。

    4. 將 <xref:System.TimeZoneInfo.AdjustmentRule> 物件指派給物件的陣列 <xref:System.TimeZoneInfo.AdjustmentRule> 。

2. 定義時區的顯示名稱。 顯示名稱會遵循相當標準的格式，在此格式中，國際標準時間 (UTC) 的時區時差會以括弧括住，後面接著可識別時區的字串、時區中的一或多個城市，或時區中的一或多個國家或地區。

3. 定義時區標準時間的名稱。 一般而言，此字串也會當做時區的識別碼使用。

4. 定義時區日光節約時間的名稱。

5. 如果您想要使用與時區標準名稱不同的識別碼，請定義時區識別碼。

6. 具現化 <xref:System.TimeSpan> 物件，該物件定義時區與 UTC 的位移。 時間晚于 UTC 的時區具有正數位移。 時間早于 UTC 時間的時區具有負位移。

7. 呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> 方法，以將新的時區具現化。

## <a name="example"></a>範例

下列範例會定義美國中部標準時區，其中包含各種時間間隔從1918到目前的調整規則。

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

在此範例中建立的時區具有多個調整規則。 請務必小心，以確保任何調整規則的有效開始和結束日期都不會與另一個調整規則的日期重迭。 如果有重迭， <xref:System.InvalidTimeZoneException> 則會擲回。

若為浮動調整規則，則會將值5傳遞給 `week` 方法的參數， <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> 以指出轉換會在特定月份的最後一周進行。

在建立 <xref:System.TimeZoneInfo.AdjustmentRule> 要在方法呼叫中使用的物件陣列 <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> 時，程式碼可以將陣列初始化為要為時區建立的調整數目所需的大小。 相反地，這個程式碼範例會呼叫 <xref:System.Collections.Generic.List%601.Add%2A> 方法，將每個調整規則加入至物件的泛型 <xref:System.Collections.Generic.List%601> 集合 <xref:System.TimeZoneInfo.AdjustmentRule> 。 然後，程式碼會呼叫 <xref:System.Collections.Generic.List%601.CopyTo%2A> 方法，將這個集合的成員複製到陣列。

此範例也會使用 <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> 方法來定義固定日期的調整。 這與呼叫 <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> 方法類似，只不過它只需要轉換參數的時間、月和日。

您可以使用下列程式碼來測試範例：

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

- 匯入下列命名空間：

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](index.md)
- [時區概觀](time-zone-overview.md)
- [如何：建立沒有調整規則的時區](create-time-zones-without-adjustment-rules.md)
