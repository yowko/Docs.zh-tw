---
title: 如何：存取預先定義的 UTC 和當地時區物件
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
ms.openlocfilehash: ebb07800b2a35f4faf312dc55b8c5679079b4b68
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291405"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>如何：存取預先定義的 UTC 和當地時區物件

<xref:System.TimeZoneInfo>類別提供兩個屬性： <xref:System.TimeZoneInfo.Utc%2A> 和 <xref:System.TimeZoneInfo.Local%2A> ，讓您的程式碼能夠存取預先定義的時區物件。 本主題討論如何存取這些屬性所傳回的 <xref:System.TimeZoneInfo> 物件。

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>存取國際標準時間 (UTC) TimeZoneInfo 物件

1. 使用 `static` （ `Shared` 在 Visual Basic 中） <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> 屬性來存取國際標準時間。

2. <xref:System.TimeZoneInfo>請繼續透過屬性來存取國際標準時間，而不是將屬性傳回的物件指派給物件變數 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> 。

### <a name="to-access-the-local-time-zone"></a>存取當地時區

1. 使用 `static` （ `Shared` 在 Visual Basic 中） <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 屬性來存取本機系統時區。

2. <xref:System.TimeZoneInfo>請繼續透過屬性來存取當地時區，而不是將屬性傳回的物件指派給物件變數 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 。

## <a name="example"></a>範例

下列程式碼會使用 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 和 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> 屬性轉換美國及加拿大東部標準時區的時間，以及對主控台顯示時區名稱。

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

您應該一律透過屬性來存取當地時區， <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 而不是將當地時區指派給 <xref:System.TimeZoneInfo> 物件變數。 同樣地，您應該一律透過屬性存取國際標準時間， <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> 而不是將 UTC 區域指派給 <xref:System.TimeZoneInfo> 物件變數。 這可避免 <xref:System.TimeZoneInfo> 物件變數因呼叫方法而失效 <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> 。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

- <xref:System>使用語句匯入的命名空間 `using` （在 c # 程式碼中為必要項）。

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](index.md)
- [尋找定義于本機系統的時區](finding-the-time-zones-on-local-system.md)
- [如何：具現化 TimeZoneInfo 物件](instantiate-time-zone-info.md)
