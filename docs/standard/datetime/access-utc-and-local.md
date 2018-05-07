---
title: 如何： 存取預先定義的 UTC 與本地時間區域物件
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
ms.openlocfilehash: b7ddf7ba69d8bed84f62d329fd26794e2641d954
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>如何： 存取預先定義的 UTC 與本地時間區域物件

<xref:System.TimeZoneInfo>類別提供兩個屬性：<xref:System.TimeZoneInfo.Utc%2A>和<xref:System.TimeZoneInfo.Local%2A>，，讓您的程式碼存取預先定義的時區物件。 本主題討論如何存取這些屬性所傳回的 <xref:System.TimeZoneInfo> 物件。

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>存取國際標準時間 (UTC) TimeZoneInfo 物件

1. 使用`static`(`Shared`在 Visual Basic 中)<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>屬性來存取國際標準時間。

2. 與其指派<xref:System.TimeZoneInfo>物件屬性所傳回的物件變數，以繼續存取透過國際標準時間<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>屬性。

### <a name="to-access-the-local-time-zone"></a>存取當地時區

1. 使用`static`(`Shared`在 Visual Basic 中)<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性來存取本機系統時區。

2. 與其指派<xref:System.TimeZoneInfo>物件屬性所傳回的物件變數，以繼續存取透過本地時區<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性。

## <a name="example"></a>範例

下列程式碼會使用 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 和 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> 屬性轉換美國及加拿大東部標準時區的時間，以及對主控台顯示時區名稱。

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

您一定要存取透過本地時區<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性，而不是指定本地時間區域以<xref:System.TimeZoneInfo>物件變數。 同樣地，您應該一律存取透過國際標準時間<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>至區域的屬性，而非指定 UTC<xref:System.TimeZoneInfo>物件變數。 這可防止<xref:System.TimeZoneInfo>物件變數，使其免於無效的呼叫所<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>方法。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* 對 system.core.dll 的參考無法加入至專案。

* 確認<xref:System>以匯入命名空間`using`陳述式 （C# 程式碼所需）。

## <a name="see-also"></a>另請參閱

[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[尋找本機系統上所定義的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[如何： 具現化 TimeZoneInfo 物件](../../../docs/standard/datetime/instantiate-time-zone-info.md)
