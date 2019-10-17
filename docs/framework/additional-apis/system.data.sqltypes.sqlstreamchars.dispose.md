---
title: SqlStreamChars. Dispose （布林值）方法（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 44dc97835b8a7141064e8de4d2d5325c40be5a34
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395759"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a>SqlStreamChars Dispose （布林值）方法

在衍生類別中覆寫時，釋放資料流程所使用的資源。 包含這個方法的元件與 SQLAccess 具有 friend 關聯性。 其目的是要供 SQL Server 使用。 若為其他資料庫，請使用該資料庫所提供的裝載機制。

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a>參數

`disposing`\
`true` 表示釋放 Managed 和 Unmanaged 資源，`false` 則表示只釋放 Unmanaged 資源。

## <a name="remarks"></a>備註

> [!WARNING]
> @No__t-0 方法是私用的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**元件：** System.web （在 System.web 中）

**.NET Framework 版本：** 自2.0 開始提供。
