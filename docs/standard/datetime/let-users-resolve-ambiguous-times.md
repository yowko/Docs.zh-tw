---
title: 作法：讓使用者解決模稜兩可的時間
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET], ambiguous time
- ambiguous time [.NET]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: 9eb1f576fd10b22383d77b90f63009fef41582d6
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063582"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>作法：讓使用者解決模稜兩可的時間

不明確的時間是指對應到多個國際標準時間 (UTC) 的時間。 發生時機是往回調整時鐘時間，例如從時區的日光節約時間轉換到其標準時間期間。 處理不明確的時間時，您可以執行下列其中一項：

- 如果不明確的時間是使用者所輸入的資料項目，可交由使用者解決此不明確狀況。

- 假設如何將時間對應至 UTC。 例如，您可以假設不明確的時間一律是以時區的標準時間表示。

本主題說明如何讓使用者解決不明確的時間。

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>讓使用者解決不明確的時間

1. 取得使用者的時間和日期輸入。

2. 呼叫 <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> 方法以判斷時間是否不明確。

3. 如果時間不明確，請呼叫 <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> 方法來取出物件的陣列 <xref:System.TimeSpan> 。 陣列中的每個元素都包含不明確時間可以對應的 UTC 時差。

4. 讓使用者選取想要的位移。

5. 將當地時間減去使用者所選取的位移，以取得 UTC 日期和時間。

6. `static` `Shared` 在 Visual Basic .net) 方法中呼叫 (<xref:System.DateTime.SpecifyKind%2A> ，以將 UTC 日期和時間值的 <xref:System.DateTime.Kind%2A> 屬性設定為 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> 。

## <a name="example"></a>範例

下列範例會提示使用者輸入日期和時間，若其不明確，可讓使用者選取不明確時間所對應的 UTC 時間。

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

範例程式碼的核心會使用 <xref:System.TimeSpan> 物件陣列來指出不明確時間與 UTC 之間可能的位移。 不過，這些位移不可能對使用者具有任何意義。 若要釐清位移的意義，程式碼也會註明位移是否代表當地時區的標準時間或其日光節約時間。 此程式碼會藉由比較位移與屬性的值，來判斷哪一個時間是標準的，而哪個時間是日光節約時間 <xref:System.TimeZoneInfo.BaseUtcOffset%2A> 。 這個屬性指出 UTC 與時區標準時間的差異。

在此範例中，本地時區的所有參考都是透過屬性進行，而 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 本地時區絕不會指派給物件變數。 這是建議的作法，因為呼叫 <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> 方法會讓本地時區指派的任何物件失效。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

- <xref:System>使用 `using` c # 程式碼) 所需的語句來匯入命名空間 (。

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](index.md)
- [如何：解決不明確的時間](resolve-ambiguous-times.md)
