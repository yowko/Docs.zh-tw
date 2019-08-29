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
ms.openlocfilehash: 6ae739d3c5dd233c2129950666846979edfba370
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106679"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>作法：建立有調整規則的時區

應用程式所需的精確時區資訊可能因下列幾個原因而不存在於特定系統上:

- 本機系統的登錄中從未定義過時區。

- 已從登錄中修改或移除時區的相關資料。

- 時區對於特定的歷程記錄期間, 沒有時區調整的精確資訊。

在這些情況下, 您可以呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法來定義應用程式所需的時區。 您可以使用這個方法的多載來建立具有或不含調整規則的時區。 如果時區支援日光節約時間, 您可以使用固定或浮動調整規則來定義調整。 (如需這些詞彙的定義, 請參閱時區[總覽](../../../docs/standard/datetime/time-zone-overview.md)中的「時區詞彙」一節)。

> [!IMPORTANT]
> 藉由呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法所建立的自訂時間區域不會新增至登錄。 相反地, 它們只能透過<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法呼叫所傳回的物件參考來存取。

本主題說明如何建立具有調整規則的時區。 若要建立不支援日光節約時間調整規則的時區, 請參閱[如何:建立沒有調整規則](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)的時區。

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>建立具有浮動調整規則的時區

1. 針對每個調整 (也就是在特定時間間隔內, 每個轉換遠離或回到標準時間), 執行下列動作:

    1. 定義時區調整的開始轉換時間。

       您必須呼叫<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>方法, 並傳遞一個<xref:System.DateTime>值來定義轉換的時間、定義轉換之月份的整數值、定義<xref:System.DayOfWeek>轉換發生之周的整數值, 以及定義發生轉換之周間日期的值。 這個方法呼叫會具<xref:System.TimeZoneInfo.TransitionTime>現化物件。

    2. 定義時區調整的結束轉換時間。 這需要對<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>方法進行另一個呼叫。 這個方法呼叫會具現<xref:System.TimeZoneInfo.TransitionTime>化第二個物件。

    3. 呼叫方法, 並將調整的有效開始和結束日期<xref:System.TimeSpan> 、定義轉換中時間量的物件, 以及定義日光節約轉換時所用的兩<xref:System.TimeZoneInfo.TransitionTime>個物件傳遞給它。 <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A>發生時間。 這個方法呼叫會具<xref:System.TimeZoneInfo.AdjustmentRule>現化物件。

    4. 將物件指派給物件的<xref:System.TimeZoneInfo.AdjustmentRule>陣列。 <xref:System.TimeZoneInfo.AdjustmentRule>

2. 定義時區的顯示名稱。 顯示名稱遵循相當標準的格式, 其中時區與國際標準時間 (UTC) 的位移會括在括弧中, 後面接著可識別時區的字串、時區中的一或多個城市, 或一或多個 cou時區中的 ntries 或區域。

3. 定義時區標準時間的名稱。 通常, 這個字串也會當做時區的識別碼使用。

4. 定義時區的日光節約時間名稱。

5. 如果您想要使用與時區標準名稱不同的識別碼, 請定義時區識別碼。

6. 具現化物件, 其定義時區與 UTC 的位移。 <xref:System.TimeSpan> 時間與 UTC 時間較晚的時區具有正位移。 具有早于 UTC 時間的時區具有負位移。

7. <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>呼叫方法, 以具現化新的時區。

## <a name="example"></a>範例

下列範例會定義美國中部標準時區, 其中包含從1918到目前為止的各種時間間隔的調整規則。

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

在此範例中建立的時區有多個調整規則。 請務必小心, 以確保任何調整規則的有效開始和結束日期不會與另一個調整規則的日期重迭。 如果有重迭, <xref:System.InvalidTimeZoneException>就會擲回。

對於浮動調整規則, 值5會傳遞至`week` <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>方法的參數, 以指出轉換會在特定月份的最後一周發生。

在建立要<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>在方法<xref:System.TimeZoneInfo.AdjustmentRule>呼叫中使用的物件陣列時, 程式碼可以將陣列初始化為要為時區建立的調整數目所需的大小。 相反地, 此程式碼範例<xref:System.Collections.Generic.List%601.Add%2A>會呼叫方法, 以將每個調整<xref:System.Collections.Generic.List%601>規則新增<xref:System.TimeZoneInfo.AdjustmentRule>至物件的泛型集合。 然後, 程式碼會<xref:System.Collections.Generic.List%601.CopyTo%2A>呼叫方法, 將這個集合的成員複製到陣列。

此範例也會使用<xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A>方法來定義固定日期的調整。 這類似于呼叫<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>方法, 不同之處在于它只需要時間、月份和轉換參數的日期。

您可以使用下列程式碼來測試此範例:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

- 匯入下列命名空間:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](../../../docs/standard/datetime/index.md)
- [時區概觀](../../../docs/standard/datetime/time-zone-overview.md)
- [如何：建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
