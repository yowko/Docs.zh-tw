---
title: "尋找定義於本機系統的時區"
description: "尋找定義於本機系統的時區"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3a6ee323-f3cf-486d-aa0c-103931f1eba9
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: e61017e2a0e26295c3be7e8265674b1a5d2ae5a3
ms.lasthandoff: 03/02/2017

---

# <a name="finding-the-time-zones-defined-on-a-local-system"></a>尋找定義於本機系統的時區

[System.TimeZoneInfo](xref:System.TimeZoneInfo) 類別不會公開公用建構函式。 如此一來，`new` 關鍵字不能用來建立新的 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件。 相反地，[TimeZoneInfo](xref:System.TimeZoneInfo) 物件的具現化方式是從作業系統擷取預先定義時區的詳細資訊。 本主題討論如何從作業系統所儲存的資料來具現化時區。 此外，[TimeZoneInfo](xref:System.TimeZoneInfo) 類別的 `static` (在 Visual Basic 中為 `Shared`) 屬性提供國際標準時間 (UTC) 及當地時區的存取。

## <a name="accessing-individual-time-zones"></a>存取個別時區

[TimeZoneInfo](xref:System.TimeZoneInfo) 類別提供兩個預先定義的時區物件，該物件代表 UTC 時間和當地時區。 它們分別從 [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) 和 [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) 屬性所提供。 如需存取 UTC 或當地時區的指示，請參閱[如何：存取預先定義的 UTC 和當地時區物件](access-utc-and-local.md)。 

您也可以具現化 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件，該物件代表作業系統所定義的任何時區。 如需特定時區物件具現化的指示，請參閱[如何：具現化 TimeZoneInfo 物件](instantiate-time-zone-info.md)。

## <a name="time-zone-identifiers"></a>時區識別項

時區識別項是唯一識別時區的索引鍵欄位。 雖然大部分的索引鍵相對較短，但時區識別項相較之下就很長。 在大部分情況下，其值會對應到 [TimeZoneInfo.StandardName](xref:System.TimeZoneInfo.StandardName) 屬性，用來提供時區標準時間的名稱。 不過仍有例外狀況。 若要確定您提供了有效的識別項，最好是列舉系統上可用的時區，並記下其相關聯的識別項。 如需列舉時區的指示，請參閱[如何：列舉電腦上展示的時區](enumerate-time-zones.md)。

## <a name="see-also"></a>另請參閱

[日期、時間及時區](index.md)

[如何：存取預先定義的 UTC 及當地時區物件](access-utc-and-local.md)

[如何：具現化 TimeZoneInfo 物件](instantiate-time-zone-info.md)

[如何：列舉電腦上既有的時區](enumerate-time-zones.md)

[轉換各時區的時間](converting-between-time-zones.md)
