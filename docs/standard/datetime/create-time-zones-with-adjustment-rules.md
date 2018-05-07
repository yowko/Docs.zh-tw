---
title: 如何： 建立有調整規則的時區
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
ms.openlocfilehash: c63b93e0dc587571605edb305979b8f97bf54cb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>如何： 建立有調整規則的時區

為應用程式所需的精確的時區資訊可能不存在特定的系統上有幾個原因：

* 時區永遠不會在本機系統登錄中已定義。

* 已經修改或移除登錄中時區的相關資料。

* 時區並沒有特定的歷程記錄期間時區調整的正確資訊。

在這些情況下，您可以呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法，以定義應用程式所需的時區。 您可以使用這個方法的多載來建立具有或沒有調整規則的時區。 如果時區支援日光節約時間，您可以定義其中一個固定或浮動調整規則的調整。 (如需這些詞彙的定義，請參閱 < 時區詞彙 」 一節[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)。)

> [!IMPORTANT]
> 藉由呼叫建立的自訂時區<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法不會加入至登錄。 相反地，他們可以只透過存取所傳回的物件參考<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法呼叫。

本主題示範如何建立有調整規則的時區。 若要建立不支援日光節約時間調整規則的時區，請參閱[How to： 建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)。

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>若要建立採用浮動調整規則的時區

1. 每個調整 （也就是，針對每個轉換遠離和一段特定時間間隔回標準時間），執行下列動作：

    1. 定義時區調整開始轉換的時間。

       您必須呼叫<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>方法並將它傳遞<xref:System.DateTime>值，其定義的轉換、 定義轉換的月份的整數值、 整數值，定義轉換發生的當週的時間和<xref:System.DayOfWeek>定義轉換發生的一週天數的值。 這個方法呼叫會具現化<xref:System.TimeZoneInfo.TransitionTime>物件。

    2. 定義結束轉換的時區調整的時間。 這需要另一個呼叫<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>方法。 這個方法呼叫會具現化第二個<xref:System.TimeZoneInfo.TransitionTime>物件。

    3. 呼叫<xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A>方法並將它傳遞的有效開始和結束日期的調整，<xref:System.TimeSpan>物件，在轉換中，以及兩個定義的時間量<xref:System.TimeZoneInfo.TransitionTime>物件，以定義何時套用日光節約時間來回轉換發生時間。 這個方法呼叫會具現化<xref:System.TimeZoneInfo.AdjustmentRule>物件。

    4. 指派<xref:System.TimeZoneInfo.AdjustmentRule>物件的陣列<xref:System.TimeZoneInfo.AdjustmentRule>物件。

2. 定義時區的顯示名稱。 顯示名稱會遵循國際標準時間 (UTC) 時區的位移加上括弧和後面的字串，識別時區，一或多個時區中，或其中一個城市的多個 cou 相當標準格式ntries 或時區中的區域。

3. 定義時區標準時間名稱。 一般而言，這個字串也做時區的識別項。

4. 定義時區的日光節約時間名稱。

5. 如果您想要使用不同的識別項與時區的標準名稱，定義時區識別項。

6. 具現化<xref:System.TimeSpan>定義與 UTC 的時區時差的物件。 較晚於 UTC 的時區有正面的位移。 時間早於 UTC 的時區有了負數的位移。

7. 呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>方法來具現化新的時區。

## <a name="example"></a>範例

下列範例會定義包含各種不同的時間間隔從 1918年至目前的調整規則的美國中部標準時區。

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

此範例中所建立的時區有多項調整規則。 小心以確保的有效開始和結束日期的任何調整規則未重疊的另一項調整規則的日期。 如果沒有重疊，<xref:System.InvalidTimeZoneException>就會擲回。

5 的值傳遞至浮點調整規則，`week`參數<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>方法，以表示轉換發生在特定月份的最後一週。

在中建立的陣列<xref:System.TimeZoneInfo.AdjustmentRule>物件中使用<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>方法呼叫的程式碼可以初始化數個調整時區建立所需的大小的陣列。 相反地，這個程式碼範例會呼叫<xref:System.Collections.Generic.List%601.Add%2A>方法，將每個調整規則加入至泛型<xref:System.Collections.Generic.List%601>集合<xref:System.TimeZoneInfo.AdjustmentRule>物件。 然後程式碼會呼叫<xref:System.Collections.Generic.List%601.CopyTo%2A>方法，將此集合的成員複製到陣列。

此範例也會使用<xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A>方法，以定義固定日期調整。 這是類似於呼叫<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>方法，但是它需要只時間、 月和日轉換參數。

可以使用下列程式碼來測試範例：

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* 對 system.core.dll 的參考無法加入至專案。

* 應該是匯入下列命名空間：

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>另請參閱

[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)
[How to： 建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
