---
title: 如何： 解決模稜兩可的時間
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb09b1f087e0a0f726d32d85e06cfb2a9ec741a8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863130"
---
# <a name="how-to-resolve-ambiguous-times"></a>如何： 解決模稜兩可的時間

不明確的時間是指對應到多個國際標準時間 (UTC) 的時間。 發生時機是往回調整時鐘時間，例如從時區的日光節約時間轉換到其標準時間期間。 處理模稜兩可的時間時，您可以執行下列其中一項：

* 假設如何將時間對應至 UTC。 例如，您可以假設不明確的時間一律是以時區的標準時間表示。

* 如果不明確的時間是使用者所輸入的資料項目，可交由使用者解決此不明確狀況。

本主題說明如何解決不明確的時間，假設它代表時區標準時間。

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>將不明確的時間對應至時區標準時間

1. 呼叫<xref:System.TimeZoneInfo.IsAmbiguousTime%2A>方法，以判斷時間是否模稜兩可。

2. 如果時間是模稜兩可，減去的時間<xref:System.TimeSpan>時區所傳回的物件<xref:System.TimeZoneInfo.BaseUtcOffset%2A>屬性。

3. 呼叫`static`(`Shared`在 Visual Basic.NET)<xref:System.DateTime.SpecifyKind%2A>方法，以設定 UTC 日期和時間值的<xref:System.DateTime.Kind%2A>屬性設<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>。

## <a name="example"></a>範例

下列範例說明如何將模稜兩可的時間轉換為 UTC，假設它代表當地時區的標準時間。

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

此範例包含名為的方法`ResolveAmbiguousTime`，決定是否<xref:System.DateTime>傳遞給它的值是模稜兩可。 如果值為模稜兩可，則方法會傳回<xref:System.DateTime>值，表示相對應的 UTC 時間。 此方法會處理這項轉換減去當地時區的值<xref:System.TimeZoneInfo.BaseUtcOffset%2A>從當地時間的屬性。

一般情況下，模稜兩可的時間由呼叫<xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A>方法來擷取陣列<xref:System.TimeSpan>物件都包含模稜兩可的時間可能 UTC 位移。 不過，此範例會進行任意假設，即不明確的時間應該一律對應至時區標準時間。 <xref:System.TimeZoneInfo.BaseUtcOffset%2A>屬性會傳回 UTC 與時區標準時間之間的位移。

在此範例中，本地時區的所有參考都會都經過<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性; 當地區域永遠不會指派給物件變數。 這是建議的作法，因為呼叫<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>方法失效的當地時區指派給任何物件。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* 對 System.Core.dll 的參考加入至專案。

* 該<xref:System>命名空間匯入與`using`陳述式 （C# 程式碼所需）。

## <a name="see-also"></a>另請參閱

* [日期、時間和時區](../../../docs/standard/datetime/index.md)
* [操作說明：讓使用者解決模稜兩可的時間](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
