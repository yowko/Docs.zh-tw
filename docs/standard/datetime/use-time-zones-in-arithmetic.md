---
title: 如何： 在日期和時間運算中使用時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f9d326750cdef96be1aa6055d46b4ac08ec7a0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574578"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>如何： 在日期和時間運算中使用時區

一般來說，當您執行的日期和時間算術使用<xref:System.DateTime>或<xref:System.DateTimeOffset>結果的值，並不會反映任何時區調整規則。 這是 true 即使的日期和時間值的時區是清楚識別 (例如，當<xref:System.DateTime.Kind%2A>屬性設定為<xref:System.DateTimeKind.Local>)。 本主題說明如何執行屬於特定時區的日期和時間值的算術運算。 算術運算的結果將反映時區調整規則。

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>將調整規則套用至日期和時間運算

1. 實作某種方法，以將日期和時間值與所屬時區緊密結合。 例如，宣告包含日期和時間值及其時區的結構。 下列範例會使用這種方法來連結<xref:System.DateTime>具有時區的值。

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. 藉由呼叫轉換為國際標準時間 (UTC) 時間<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>方法或<xref:System.TimeZoneInfo.ConvertTime%2A>方法。

3. 對 UTC 時間執行算術運算。

4. 將時間與 utc 之間轉換為原始的時間相關的時區，藉由呼叫<xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>方法。

## <a name="example"></a>範例

下列範例將兩個小時三十分鐘新增至 2008 年 3 月 9 日凌晨 1:30 中央標準時區。 時區轉換為日光節約時間會在三十分鐘後，也就是 2008 年 3 月 9 日 凌晨 5:00。 由於本範例依照上一節所列的四個步驟進行，因此會正確回報產生的時間 2008 年 3 月 9 日 凌晨 5:00。

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

同時<xref:System.DateTime>和<xref:System.DateTimeOffset>值會從其可能所屬的任意時區解除關聯。 若要透過自動套用時區調整規則來執行日期和時間運算，則必須立即識別任何日期和時間值所屬的時區。 這表示日期和時間及其相關聯時區必須緊密結合。 有幾個方式可做到這點，包括下列各項︰

* 假設應用程式中使用的所有時間都是屬於特定時區。 雖然適用於某些情況，但是這種方式提供的彈性有限，可攜性也可能有限。

* 定義一種類型，而這個類型透過將日期和時間與其相關聯時區都包含為類型的欄位來緊密結合兩者。 程式碼範例中使用這種方式，以定義將日期和時間以及時區儲存在兩個成員欄位中的結構。

此範例說明如何在上執行算術運算<xref:System.DateTime>值，使時區調整規則會套用到結果。 不過，<xref:System.DateTimeOffset>可以輕鬆地使用值。 下列範例說明如何在原始的範例程式碼可能是改寫以使用<xref:System.DateTimeOffset>而不是<xref:System.DateTime>值。

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

請注意，如果這個加法只對<xref:System.DateTimeOffset>值沒有先將它轉換成 UTC，結果會反映正確的點的時間，但它的位移不會反映指定時區的時間。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* 對 system.core.dll 的參考無法加入至專案。

* 確認<xref:System>以匯入命名空間`using`陳述式 （C# 程式碼所需）。

## <a name="see-also"></a>另請參閱

[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[使用日期和時間執行算術運算](../../../docs/standard/datetime/performing-arithmetic-operations.md)
