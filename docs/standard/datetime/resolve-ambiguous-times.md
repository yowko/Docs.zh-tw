---
title: "如何： 解決模稜兩可的時間"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 251f1914b131c5deed194ad7f3fb068c1d9b27c5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-resolve-ambiguous-times"></a>如何： 解決模稜兩可的時間

不明確的時間是指對應到多個國際標準時間 (UTC) 的時間。 發生時機是往回調整時鐘時間，例如從時區的日光節約時間轉換到其標準時間期間。 處理模稜兩可的時間時，您可以執行下列其中一項：

* 假設如何將時間對應至 UTC。 例如，您可以假設不明確的時間一律是以時區的標準時間表示。

* 如果不明確的時間是使用者所輸入的資料項目，可交由使用者解決此不明確狀況。

本主題說明如何解決模稜兩可的時間所假設代表時區的標準時間。

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>將不明確的時間對應至時區標準時間

1. 呼叫<xref:System.TimeZoneInfo.IsAmbiguousTime%2A>方法，以判斷時間是否模稜兩可。

2. 如果模稜兩可的時間，減去的時間從<xref:System.TimeSpan>傳回時區的物件<xref:System.TimeZoneInfo.BaseUtcOffset%2A>屬性。

3. 呼叫`static`(`Shared`在 Visual Basic.NET)<xref:System.DateTime.SpecifyKind%2A>方法，以設定的 UTC 日期和時間值的<xref:System.DateTime.Kind%2A>屬性<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>。

## <a name="example"></a>範例

下列範例說明如何將模稜兩可的時間轉換成 UTC 的假設代表本地時區的標準時間。

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

此範例包含名為的方法`ResolveAmbiguousTime`，決定是否<xref:System.DateTime>傳遞給它的值模稜兩可。 如果值為模稜兩可，則方法會傳回<xref:System.DateTime>值，表示對應的 UTC 時間。 方法會藉由減去本地時區的值來處理這項轉換<xref:System.TimeZoneInfo.BaseUtcOffset%2A>屬性從本地時間。

一般情況下，模稜兩可的時間由呼叫<xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A>方法來擷取陣列<xref:System.TimeSpan>物件，其中包含可能模稜兩可的時間的 UTC 位移。 不過，此範例會進行任意假設，即不明確的時間應該一律對應至時區標準時間。 <xref:System.TimeZoneInfo.BaseUtcOffset%2A>屬性傳回 UTC 時區的標準時間之間的位移。

在此範例中，所有參考的當地時區都透過<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性; 區域永遠不會指派給物件變數的本機時間。 這是建議的作法，因為呼叫<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>方法會導致無效的當地時區指派給任何物件。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* 對 system.core.dll 的參考無法加入至專案。

* 確認<xref:System>以匯入命名空間`using`陳述式 （C# 程式碼所需）。

## <a name="see-also"></a>另請參閱

[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[如何： 讓使用者解決模稜兩可的時間](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
