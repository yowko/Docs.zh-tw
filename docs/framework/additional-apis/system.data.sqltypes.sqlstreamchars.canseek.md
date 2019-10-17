---
title: SqlStreamChars. CanSeek 屬性（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: eb32978f62b7d46f0abf715e2bca347592c0fda8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395771"
---
# <a name="sqlstreamcharscanseek-property"></a>SqlStreamChars. CanSeek 屬性

在衍生類別中覆寫時，取得值，指出目前的資料流程是否支援搜尋作業。 包含此屬性的元件與 SQLAccess 具有 friend 關聯性。 其目的是要供 SQL Server 使用。 若為其他資料庫，請使用該資料庫所提供的裝載機制。

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>屬性值

<xref:System.Boolean>\
如果目前的流支援搜尋作業，則 `true`：否則，`false`。

## <a name="remarks"></a>備註

> [!WARNING]
> @No__t-0 屬性是私用的，而且不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此屬性。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**元件：** System.web （在 System.web 中）

**.NET Framework 版本：** 自2.0 開始提供。
