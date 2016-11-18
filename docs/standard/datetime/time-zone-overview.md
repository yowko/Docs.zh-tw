---
title: "時區概觀"
description: "時區概觀"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e3a10f62-d403-4441-8621-adc964e32c07
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 67d77b80c2517da1c553094689eaf08c0c29078b

---

# <a name="time-zone-overview"></a>時區概觀

[System.TimeZoneInfo](xref:System.TimeZoneInfo) 類別可簡化時區感知應用程式的建立。 [TimeZoneInfo](xref:System.TimeZoneInfo) 類別支援處理當地時區和國際標準時間 (UTC)，以及登錄中預先定義之資訊的任何時區。 您也可以使用 [TimeZoneInfo](xref:System.TimeZoneInfo) 來定義系統沒有相關資訊的自訂時區。

## <a name="time-zone-essentials"></a>時區基本功能

時區是使用相同時間的地理區域。 相鄰時區一般但不一定會相差一個小時。 任何全世界時區的時間可以表示為與國際標準時間 (UTC) 的位移。

許多全世界的時區都支援日光節約時間。 日光節約時間會嘗試將日光時數延到最長，方法是將春天或夏初的時間前進一個小時，並在夏末或秋天回復正常 (或標準) 時間。 這些標準時間的變更稱為調整規則。

透過固定或浮動調整規則，可以定義轉換至及轉換自特定時區的日光節約時間。 固定調整規則會設定每年轉換至或轉換自日光節約時間的特定日期。 例如，每年在 10 月 25 日從日光節約時間到標準時間的轉換會遵循固定調整規則。 更常見的是浮動調整規則，可設定在特定月份特定週特定一天轉換至或轉換自日光節約時間。 例如，在三月第三個星期日從標準時間到日光節約時間的轉換會遵循浮動調整規則。

對於支援調整規則的時區，轉換至和轉換自日光節約時間會建立兩種異常時間︰無效的時間和不明確的時間。 無效時間是從標準時間轉換到日光節約時間所建立的不存在時間。 例如，如果這項轉換發生在特定日的凌晨 2:00， 並將時間變更為凌晨 3:00，則凌晨 2:00 與凌晨 2:59:99 之間的每個時間間隔 無效。 不明確的時間是可以對應至單一時區中兩個不同時間的時間。 它是透過從日光節約時間轉換到標準時間所建立。 例如，如果這項轉換發生在特定日的凌晨 2:00， 並將時間變更為凌晨 1:00，則凌晨 1:00 與凌晨 1:59:99 之間的每個時間間隔 可以解譯為標準時間或日光節約時間。 

## <a name="time-zone-terminology"></a>時區術語

下表定義在使用時區以及開發時區感知應用程式時常用的詞彙。

詞彙 | 定義
---- | ----------
調整規則 | 一種規則，定義何時從標準時間轉換為日光節約時間，以及何時從日光節約時間轉換回標準時間。 每個調整規則都會有定義規則何時就緒的開始和結束日期 (例如，調整規則是從 1986 年 1 月 1 日到 2020 年 12 月 31 日就緒)、差異 (標準時間因套用調整規則而變更的時間量)，以及調整期間進行轉換之特定日期和時間的相關資訊。 轉換可以遵循固定規則或浮動規則。
不明確的時間 | 可以對應至單一時區中兩個不同時間的時間。 發生時機是往回調整時鐘時間，例如從時區的日光節約時間轉換到其標準時間期間。 例如，如果這項轉換發生在特定日的凌晨 2:00， 並將時間變更為凌晨 1:00，則凌晨 1:00 與凌晨 1:59:99 之間的每個時間間隔 可以解譯為標準時間或日光節約時間。 
固定規則 | 設定在特定日期轉換至或轉換自日光節約時間的調整規則。 例如，每年在 10 月 25 日從日光節約時間到標準時間的轉換會遵循固定調整規則。
浮動規則 | 設定在特定月份特定週特定一天轉換至或轉換自日光節約時間的調整規則。 例如，在三月第三個星期日從標準時間到日光節約時間的轉換會遵循浮動調整規則。
無效時間 | 不存在時間是從標準時間轉換到日光節約時間的成品。 發生時機是往前調整時鐘時間，例如從時區標準時間轉換到其日光節約時間。 例如，如果這項轉換發生在特定日的凌晨 2:00， 並將時間變更為凌晨 3:00，則凌晨 2:00 與凌晨 2:59:99 之間的每個時間間隔 無效。
轉換時間 | 特定時區中特定時間變更的相關資訊，例如從日光節約時間變更為標準時間，或從標準時間變更為日光節約時間。

## <a name="time-zones-and-the-timezoneinfo-class"></a>時區和 TimeZoneInfo 類別

在 .NET 中，[System.TimeZoneInfo](xref:System.TimeZoneInfo) 物件根據作業系統所提供的資訊來代表時區。 [TimeZoneInfo](xref:System.TimeZoneInfo) 類別與作業系統的相依性表示時區感知應用程式不能是所有作業系統上定義的特定時區。 因此，嘗試具現化特定時區 (非當地時區或代表 UTC 的時區) 應該使用例外狀況處理。 如果無法具現化必要 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件，則它也應該提供某種方法來繼續應用程式。

因為每個時區都會具備與 UTC 的基底位移，以及具備反映任何現有調整規則之與 UTC 的位移，所以某個時區的時間可以輕鬆地轉換為另一個時區的時間。 基於此目的，[TimeZoneInfo](xref:System.TimeZoneInfo) 物件包含數種轉換方法，包含︰

* [ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo))，會將 [System.DateTime](xref:System.DateTime) 轉換為特定時區的時間。

* [ConvertTime(DateTime, TimeZoneInfo, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo,System.TimeZoneInfo))，會將 [DateTime](xref:System.DateTime) 從某個時區轉換為另一個時區。

* [ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo))，會將 [System.DateTimeOffset](xref:System.DateTimeOffset) 轉換為特定時區的時間。 

如需各時區間轉換時間的詳細資訊，請參閱[在各時區間轉換時間](converting-between-time-zones.md)。

## <a name="see-also"></a>另請參閱

[日期、時間及時區](index.md)


<!--HONumber=Nov16_HO3-->


