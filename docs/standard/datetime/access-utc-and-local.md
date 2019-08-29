---
title: HOW TO：存取預先定義的 UTC 和當地時區物件
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aa19118ce0837b9ce0eb523f3e086fcbcecb9e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106557"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>作法：存取預先定義的 UTC 和當地時區物件

類別提供兩個屬性: <xref:System.TimeZoneInfo.Utc%2A>和<xref:System.TimeZoneInfo.Local%2A>, 讓您的程式碼能夠存取預先定義的時區物件。 <xref:System.TimeZoneInfo> 本主題討論如何存取這些屬性所傳回的 <xref:System.TimeZoneInfo> 物件。

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>存取國際標準時間 (UTC) TimeZoneInfo 物件

1. `static`使用 (`Shared`在 Visual Basic 中) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>屬性來存取國際標準時間。

2. 請繼續<xref:System.TimeZoneInfo> <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>透過屬性來存取國際標準時間, 而不是將屬性傳回的物件指派給物件變數。

### <a name="to-access-the-local-time-zone"></a>存取當地時區

1. `static`使用 (`Shared`在 Visual Basic 中) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性來存取本機系統時區。

2. 請繼續<xref:System.TimeZoneInfo> <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>透過屬性來存取當地時區, 而不是將屬性傳回的物件指派給物件變數。

## <a name="example"></a>範例

下列程式碼會使用 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 和 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> 屬性轉換美國及加拿大東部標準時區的時間，以及對主控台顯示時區名稱。

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

您應該一律透過<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性<xref:System.TimeZoneInfo>來存取當地時區, 而不是將當地時區指派給物件變數。 同樣地, 您應該一律透過<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>屬性存取國際標準時間, 而不是將 UTC 區域指派<xref:System.TimeZoneInfo>給物件變數。 這可避免<xref:System.TimeZoneInfo>物件變數因呼叫<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>方法而失效。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

- 使用語句匯入的<xref:System>命名空間 (在程式碼C#中為必要項)。 `using`

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](../../../docs/standard/datetime/index.md)
- [尋找定義於本機系統的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [如何：具現化 TimeZoneInfo 物件](../../../docs/standard/datetime/instantiate-time-zone-info.md)
