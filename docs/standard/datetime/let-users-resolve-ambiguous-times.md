---
title: 如何： 讓使用者解決模稜兩可的時間
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91e80f44934092007f6f842f0694789d49321446
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863547"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>如何： 讓使用者解決模稜兩可的時間

不明確的時間是指對應到多個國際標準時間 (UTC) 的時間。 發生時機是往回調整時鐘時間，例如從時區的日光節約時間轉換到其標準時間期間。 處理不明確的時間時，您可以執行下列其中一項：

* 如果不明確的時間是使用者所輸入的資料項目，可交由使用者解決此不明確狀況。

* 假設如何將時間對應至 UTC。 例如，您可以假設不明確的時間一律是以時區的標準時間表示。

本主題說明如何讓使用者解決模稜兩可的時間。

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>讓使用者解決不明確的時間

1. 取得使用者的時間和日期輸入。

2. 呼叫<xref:System.TimeZoneInfo.IsAmbiguousTime%2A>方法，以判斷時間是否模稜兩可。

3. 如果時間是模稜兩可的呼叫<xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A>方法來擷取陣列<xref:System.TimeSpan>物件。 陣列中的每個項目包含模稜兩可的時間可對應到指定 UTC 時差。

4. 讓使用者選取想要的位移。

5. 將當地時間減去使用者所選取的位移，以取得 UTC 日期和時間。

6. 呼叫`static`(`Shared`在 Visual Basic.NET)<xref:System.DateTime.SpecifyKind%2A>方法，以設定 UTC 日期和時間值的<xref:System.DateTime.Kind%2A>屬性設<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>。

## <a name="example"></a>範例

下列範例會提示使用者輸入日期和時間，若其不明確，可讓使用者選取不明確時間所對應的 UTC 時間。

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

範例程式碼的核心使用的陣列<xref:System.TimeSpan>物件，表示可能的模稜兩可的時間與 UTC 的位移。 不過，這些位移不可能對使用者具有任何意義。 若要釐清位移的意義，程式碼也會註明位移是否代表當地時區的標準時間或其日光節約時間。 程式碼會判斷是標準的時間和哪一個是日光節約時間比較位移的值與<xref:System.TimeZoneInfo.BaseUtcOffset%2A>屬性。 這個屬性指出 UTC 與時區標準時間的差異。

在此範例中，本地時區的所有參考都會都經過<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性; 當地區域永遠不會指派給物件變數。 這是建議的作法，因為呼叫<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>方法失效的當地時區指派給任何物件。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* 對 System.Core.dll 的參考加入至專案。

* 該<xref:System>命名空間匯入與`using`陳述式 （C# 程式碼所需）。

## <a name="see-also"></a>另請參閱

* [日期、時間和時區](../../../docs/standard/datetime/index.md)
* [操作說明：解決模稜兩可的時間](../../../docs/standard/datetime/resolve-ambiguous-times.md)
