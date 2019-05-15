---
title: 作法：建立有調整規則的時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: face995dbd5ba4b0b12e80bcef10a90b46c093ff
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586417"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>作法：建立有調整規則的時區

應用程式所需的精確的時區資訊可能不存在特定的系統上有幾個原因：

* 永遠不會在本機系統登錄中定義時區。

* 已修改或從登錄中移除時區相關的資料。

* 時區並沒有特定的歷程記錄時間會調整時區的精確資訊。

在這些情況下，您可以呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法，以定義應用程式所需的時區。 您可以使用此方法的多載來建立時間的時區，或沒有調整規則。 如果時區支援日光節約時間，您可以定義其中一個固定或浮動調整規則的調整。 (如需這些詞彙的定義，請參閱 < 時區詞彙 > 一節[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)。)

> [!IMPORTANT]
> 藉由呼叫建立的自訂時區<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法不會新增至登錄。 相反地，存取他們只能透過所傳回的物件參考<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法呼叫。

本主題說明如何建立有調整規則的時區。 若要建立不支援日光節約時間調整規則的時區，請參閱[How to:建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)。

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>若要建立使用浮動調整規則的時區

1. 針對每個調整 （也就是，針對每個轉換以外的位置，並回到一段特定時間間隔的標準時間），執行下列動作：

    1. 定義開始轉換的時區調整的時間。

       您必須呼叫<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>方法並將它傳遞<xref:System.DateTime>定義的轉換、 定義轉換的月份的整數值、 整數值，定義的轉換發生時，一週的時間值和<xref:System.DayOfWeek>定義轉換發生在星期幾的值。 這個方法呼叫會具現化<xref:System.TimeZoneInfo.TransitionTime>物件。

    2. 定義結束轉換時區調整的時間。 這需要另一個呼叫<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>方法。 這個方法呼叫會具現化第二個<xref:System.TimeZoneInfo.TransitionTime>物件。

    3. 呼叫<xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A>方法並將它傳遞有效的開始和結束日期的調整，<xref:System.TimeSpan>物件，在轉換和兩個定義的時間量<xref:System.TimeZoneInfo.TransitionTime>物件會定義何時從日光節約時間來回轉換發生時間。 這個方法呼叫會具現化<xref:System.TimeZoneInfo.AdjustmentRule>物件。

    4. 指派<xref:System.TimeZoneInfo.AdjustmentRule>物件的陣列<xref:System.TimeZoneInfo.AdjustmentRule>物件。

2. 定義時區的顯示名稱。 顯示名稱會遵循相當標準的格式 Coordinated Universal Time (UTC) 時區的位移以括弧括住且後面跟著識別時區，一或多個城市的時區，或其中一個或多個 cou 的字串ntries 或時區中的區域。

3. 定義時區標準時間的名稱。 一般而言，這個字串也做時區的識別項。

4. 定義時區的日光節約時間的名稱。

5. 如果您想要使用不同的識別碼，與時區的標準名稱，定義的時區識別項。

6. 具現化<xref:System.TimeSpan>定義與 UTC 的時區時差的物件。 時間會晚於 UTC 的時區有正面的位移。 與時間早於 UTC 的時區有負數位移。

7. 呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>方法具現化新的時區。

## <a name="example"></a>範例

下列範例會定義包含各種不同的時間間隔從 1918年到目前的調整規則的美國中央標準時區。

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

此範例中所建立的時區有多個調整規則。 小心以確保，有效的開始和結束日期的任何調整規則不會重疊的另一項調整規則的日期。 如果沒有重疊，<xref:System.InvalidTimeZoneException>就會擲回。

針對浮動調整規則，值 5 傳遞至`week`參數<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>方法，以表示轉換發生在特定月份的最後一週。

在中建立的陣列<xref:System.TimeZoneInfo.AdjustmentRule>物件中使用<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>方法呼叫的程式碼無法初始化數個調整時區建立所需的大小的陣列。 相反地，此程式碼範例會呼叫<xref:System.Collections.Generic.List%601.Add%2A>方法將每個調整規則新增至泛型<xref:System.Collections.Generic.List%601>的集合<xref:System.TimeZoneInfo.AdjustmentRule>物件。 程式碼會接著呼叫<xref:System.Collections.Generic.List%601.CopyTo%2A>方法，將這個集合的成員複製到陣列。

此範例也會使用<xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A>方法來定義固定日期調整。 這是類似於呼叫<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>方法，但是它需要只時間、 月和星期幾轉換參數。

此範例，可使用如下所示的程式碼進行測試：

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* 下列命名空間會匯入：

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](../../../docs/standard/datetime/index.md)
- [時區概觀](../../../docs/standard/datetime/time-zone-overview.md)
- [如何：建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
