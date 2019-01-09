---
title: SqlStreamChars.Dispose(Boolean) 方法 (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 3f2180d9a1893e651f174fff6d0f073df651e712
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152561"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a>SqlStreamChars.Dispose(Boolean) 方法

當在衍生類別中覆寫時，會釋放資料流所使用的資源。 包含這個方法的組件有 SQLAccess.dll friend 關聯性。 它適用於 SQL server。 其他資料庫，請使用該資料庫所提供的主控機制。

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a>參數

`disposing`\
`true` 表示釋放 Managed 和 Unmanaged 資源，`false` 則表示只釋放 Unmanaged 資源。

## <a name="remarks"></a>備註

> [!WARNING]
> `SqlStreamChars.Dispose`方法是私用，而且不適合直接在您的程式碼中使用。
>
> Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**組件：** System.Data （在 System.Data.dll 中)

**.NET framework 版本：** 自 2.0 起可用。