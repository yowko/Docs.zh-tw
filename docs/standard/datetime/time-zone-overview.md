---
title: 時區概觀
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], about time zones
- transition time [.NET Framework]
- TimeZoneInfo class, about TimeZoneInfo class
- time zones [.NET Framework], creating
- invalid time [.NET Framework]
- fixed rule [.NET Framework]
- ambiguous time [.NET Framework]
- floating rule [.NET Framework]
- daylight saving time [.NET Framework]
- adjustment rule [.NET Framework]
- time zones [.NET Framework], terminology
ms.assetid: c4b7ed01-5e38-4959-a3b6-ef9765d6ccf1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64fce738556fa68c54f5f7d7dcba79fc30d03bbe
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106727"
---
# <a name="time-zone-overview"></a>時區概觀

<xref:System.TimeZoneInfo>類別可簡化時區感知應用程式的建立。 <xref:System.TimeZone>類別支援使用當地時區和國際標準時間 (UTC)。 <xref:System.TimeZoneInfo>類別支援這兩個區域, 以及在登錄中預先定義了哪些資訊的時區。 您也可以使用<xref:System.TimeZoneInfo>來定義系統沒有相關資訊的自訂時區。

## <a name="time-zone-essentials"></a>時區基本知識

時區是使用相同時間的地理區域。 相鄰時區一般但不一定會相差一個小時。 任何全世界時區的時間可以表示為與國際標準時間 (UTC) 的位移。

許多全世界的時區都支援日光節約時間。 日光節約時間會嘗試將日光時數延到最長，方法是將春天或夏初的時間前進一個小時，並在夏末或秋天回復正常 (或標準) 時間。 這些標準時間的變更稱為調整規則。

透過固定或浮動調整規則，可以定義轉換至及轉換自特定時區的日光節約時間。 固定調整規則會設定每年轉換至或轉換自日光節約時間的特定日期。 例如，每年在 10 月 25 日從日光節約時間到標準時間的轉換會遵循固定調整規則。 更常見的是浮動調整規則，可設定在特定月份特定週特定一天轉換至或轉換自日光節約時間。 例如，在三月第三個星期日從標準時間到日光節約時間的轉換會遵循浮動調整規則。

對於支援調整規則的時區，轉換至和轉換自日光節約時間會建立兩種異常時間︰無效的時間和不明確的時間。 無效時間是從標準時間轉換到日光節約時間所建立的不存在時間。 例如，如果這項轉換發生在特定日的凌晨 2:00， 並將時間變更為凌晨 3:00，則凌晨 2:00 與凌晨 2:59:99 之間的每個時間間隔 無效。 不明確的時間是可以對應至單一時區中兩個不同時間的時間。 它是透過從日光節約時間轉換到標準時間所建立。 例如，如果這項轉換發生在特定日的凌晨 2:00， 並將時間變更為凌晨 1:00，則凌晨 1:00 與凌晨 1:59:99 之間的每個時間間隔 可以解譯為標準時間或日光節約時間。

## <a name="time-zone-terminology"></a>時區術語

下表定義在使用時區以及開發時區感知應用程式時常用的詞彙。

| 詞彙            | 定義 |
| --------------- | ---------- |
| 調整規則 | 一種規則，定義何時從標準時間轉換為日光節約時間，以及何時從日光節約時間轉換回標準時間。 每個調整規則都有開始和結束日期, 可定義規則的時間 (例如, 調整規則已從1986年1月1日到2006年12月31日)、差異 (標準時間因應用程式的結果而變更的時間量e 調整規則), 以及有關在調整期間發生轉換的特定日期和時間的資訊。 轉換可以遵循固定規則或浮動規則。 |
| 不明確的時間  | 可以對應至單一時區中兩個不同時間的時間。 發生時機是往回調整時鐘時間，例如從時區的日光節約時間轉換到其標準時間期間。 例如，如果這項轉換發生在特定日的凌晨 2:00， 並將時間變更為凌晨 1:00，則凌晨 1:00 與凌晨 1:59:99 之間的每個時間間隔 可以解譯為標準時間或日光節約時間。 |
| 固定規則      | 設定在特定日期轉換至或轉換自日光節約時間的調整規則。 例如，每年在 10 月 25 日從日光節約時間到標準時間的轉換會遵循固定調整規則。 |
| 浮動規則   | 設定在特定月份特定週特定一天轉換至或轉換自日光節約時間的調整規則。 例如，在三月第三個星期日從標準時間到日光節約時間的轉換會遵循浮動調整規則。 |
| 無效時間    | 不存在時間是從標準時間轉換到日光節約時間的成品。 發生時機是往前調整時鐘時間，例如從時區標準時間轉換到其日光節約時間。 例如，如果這項轉換發生在特定日的凌晨 2:00， 並將時間變更為凌晨 3:00，則凌晨 2:00 與凌晨 2:59:99 之間的每個時間間隔 無效。 |
| 轉換時間 | 特定時區中特定時間變更的相關資訊，例如從日光節約時間變更為標準時間，或從標準時間變更為日光節約時間。 |

## <a name="time-zones-and-the-timezoneinfo-class"></a>時區和 TimeZoneInfo 類別

在 .net 中, <xref:System.TimeZoneInfo>物件代表的是時區。 類別包含傳回物件陣列的<xref:System.TimeZoneInfo.AdjustmentRule> 方法。<xref:System.TimeZoneInfo.GetAdjustmentRules%2A> <xref:System.TimeZoneInfo> 此陣列的每個專案都會提供有關特定時間週期的日光節約時間來回轉換的資訊。 (對於不支援日光節約時間的時區, 此方法會傳回空陣列)。每<xref:System.TimeZoneInfo.AdjustmentRule>個物件都<xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A>有一個<xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A>和屬性, 可定義從日光節約時間轉換的特定日期和時間。 <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A>屬性會指出該轉換為固定或浮動。

.NET 會依賴 Windows 作業系統所提供的時區資訊, 並儲存在登錄中。 由於地球時區的數目, 並非所有現有的時區都是在登錄中表示。 此外, 由於登錄是動態結構, 因此可以在其中新增或移除預先定義的時區。 最後, 登錄不一定會包含歷史時區資料。 例如, 在 Windows XP 中, 登錄只包含單一時區調整的相關資料。 Windows Vista 支援動態時區資料, 這表示單一時區可以有多個調整規則, 適用于數年的特定間隔。 不過, 在 Windows Vista 登錄中定義且支援日光節約時間的大部分時區, 都只有一或兩個預先定義的調整規則。

<xref:System.TimeZoneInfo>此類別在登錄上的相依性表示, 時區感知應用程式無法確定登錄中是否定義了特定的時區。 因此，嘗試具現化特定時區 (非當地時區或代表 UTC 的時區) 應該使用例外狀況處理。 它也應該提供一些方法, 讓應用程式在無法從登錄具<xref:System.TimeZoneInfo>現化必要物件時繼續執行。

若要處理缺少所需的時區, <xref:System.TimeZoneInfo>類別會<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>包含方法, 您可以用它來建立在登錄中找不到的自訂時區。 如需建立自訂時區的詳細資訊, [請參閱如何:建立沒有調整規則](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)的時區, 以及[如何:建立具有調整規則](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)的時區。 此外, 您可以使用<xref:System.TimeZoneInfo.ToSerializedString%2A>方法, 將新建立的時區轉換成字串, 並將它儲存在資料存放區中 (例如資料庫、文字檔、登錄或應用程式資源)。 然後, 您可以使用<xref:System.TimeZoneInfo.FromSerializedString%2A>方法, 將此字串轉換回<xref:System.TimeZoneInfo>物件。 如需詳細資訊，請參閱[如何：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) , 以及[如何:從內嵌資源](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)還原時區。

因為每個時區都會具備與 UTC 的基底位移，以及具備反映任何現有調整規則之與 UTC 的位移，所以某個時區的時間可以輕鬆地轉換為另一個時區的時間。 基於此目的, <xref:System.TimeZoneInfo>物件包含數種轉換方法, 包括:

- <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>, 可將 UTC 轉換為指定時區的時間。

- <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>, 可將指定時區的時間轉換為 UTC。

- <xref:System.TimeZoneInfo.ConvertTime%2A>, 可將某個指定時區的時間轉換為另一個指定時區的時間。

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>, 其使用時區識別碼 (而不是<xref:System.TimeZoneInfo>物件) 做為參數, 將某個指定時區的時間轉換為另一個指定時區的時間。

如需各時區間轉換時間的詳細資訊，請參閱[在各時區間轉換時間](../../../docs/standard/datetime/converting-between-time-zones.md)。

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](../../../docs/standard/datetime/index.md)
