---
title: 如何： 存取預先定義的 UTC 和當地時區物件
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
ms.openlocfilehash: f074e6f6d9b11cc7d7405adced3a4523a31676fa
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086909"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>如何： 存取預先定義的 UTC 和當地時區物件

<xref:System.TimeZoneInfo>類別提供兩個屬性：<xref:System.TimeZoneInfo.Utc%2A>和<xref:System.TimeZoneInfo.Local%2A>，，讓程式碼可以存取預先定義的時區物件。 本主題討論如何存取這些屬性所傳回的 <xref:System.TimeZoneInfo> 物件。

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>存取國際標準時間 (UTC) TimeZoneInfo 物件

1. 使用`static`(`Shared` Visual Basic 中)<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>屬性存取國際標準時間。

2. 而不是指派<xref:System.TimeZoneInfo>物件屬性所傳回給物件變數，繼續存取國際標準時間透過<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>屬性。

### <a name="to-access-the-local-time-zone"></a>存取當地時區

1. 使用`static`(`Shared` Visual Basic 中)<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性存取當地系統時區。

2. 而不是指派<xref:System.TimeZoneInfo>物件屬性所傳回給物件變數，繼續存取當地時區透過<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性。

## <a name="example"></a>範例

下列程式碼會使用 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 和 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> 屬性轉換美國及加拿大東部標準時區的時間，以及對主控台顯示時區名稱。

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

您應該一律存取透過當地時區為準<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性，而不是指派當地時區指派給<xref:System.TimeZoneInfo>物件變數。 同樣地，您應該一律存取國際標準時間，透過<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>屬性，而不是指派為 UTC 時區指派給<xref:System.TimeZoneInfo>物件變數。 這可防止<xref:System.TimeZoneInfo>物件變數失效呼叫<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>方法。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* 對 System.Core.dll 的參考加入至專案。

* 該<xref:System>命名空間匯入與`using`陳述式 （C# 程式碼所需）。

## <a name="see-also"></a>另請參閱

* [日期、時間和時區](../../../docs/standard/datetime/index.md)
* [尋找定義於本機系統的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
* [操作說明：將 TimeZoneInfo 物件具現化](../../../docs/standard/datetime/instantiate-time-zone-info.md)
