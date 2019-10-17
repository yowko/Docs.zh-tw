---
title: SqlStreamChars. Length 屬性（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 2171b10d1c0eb7bcad894cc44c5103bdab18b0a5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395612"
---
# <a name="sqlstreamcharslength-property"></a>SqlStreamChars. Length 屬性

在衍生類別中覆寫時，取得目前資料流程的長度。 包含此屬性的元件與 SQLAccess 具有 friend 關聯性。 其目的是要供 SQL Server 使用。 若為其他資料庫，請使用該資料庫所提供的裝載機制。

## <a name="syntax"></a>語法

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a>屬性值

<xref:System.Int64>\
資料流的長度。

## <a name="remarks"></a>備註

> [!WARNING]
> @No__t-0 屬性是私用的，而且不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此屬性。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**元件：** System.web （在 System.web 中）

**.NET Framework 版本：** 自2.0 開始提供。
