---
title: SqlStreamChars. Flush 方法（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 38ade5ce38cfe5003b2d06c0d8bb2db1a20bc05b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395617"
---
# <a name="sqlstreamcharsflush-method"></a>SqlStreamChars. Flush 方法

當在衍生類別中覆寫時，會清除這個資料流的所有緩衝區，並造成所有緩衝資料都寫入基礎裝置。 包含這個方法的元件與 SQLAccess 具有 friend 關聯性。 其目的是要供 SQL Server 使用。 若為其他資料庫，請使用該資料庫所提供的裝載機制。

## <a name="syntax"></a>語法

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a>備註

> [!WARNING]
> @No__t-0 方法是私用的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**元件：** System.web （在 System.web 中）

**.NET Framework 版本：** 自2.0 開始提供。
