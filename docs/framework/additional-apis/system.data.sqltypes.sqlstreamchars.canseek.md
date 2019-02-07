---
title: SqlStreamChars.CanSeek 屬性 (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: bde4764af9d0160997dc202f722a12393cfa59c1
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826846"
---
# <a name="sqlstreamcharscanseek-property"></a>SqlStreamChars.CanSeek 屬性

當在衍生類別中覆寫時，取得值，指出目前資料流是否支援搜尋作業。 包含此屬性的組件有 SQLAccess.dll friend 關聯性。 它適用於 SQL server。 其他資料庫，請使用該資料庫所提供的主控機制。

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>屬性值

<xref:System.Boolean>\
`true` 如果目前資料流支援搜尋作業。否則， `false`。

## <a name="remarks"></a>備註

> [!WARNING]
> `SqlStreamChars.CanSeek`屬性是 private，而且不適合直接在您的程式碼中使用。
>
> Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**組件：** System.Data （在 System.Data.dll 中)

**.NET framework 版本：** 自 2.0 起可用。