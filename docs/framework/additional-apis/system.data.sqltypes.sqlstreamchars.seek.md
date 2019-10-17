---
title: SqlStreamChars。 Seek （Int64，SeekOrigin）方法（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: db8aba0a86c140ba62af8056011226532d415951
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395589"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a>SqlStreamChars。 Seek （Int64，SeekOrigin）方法

在衍生類別中覆寫時，設定在目前資料流的位置。 包含這個方法的元件與 SQLAccess 具有 friend 關聯性。 其目的是要供 SQL Server 使用。 若為其他資料庫，請使用該資料庫所提供的裝載機制。

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a>參數

`offset`\
相對於 `origin` 的位元組位移。

`origin`\
其中一個列舉值，表示要從中取得新位置的參考點。

## <a name="returns"></a>Returns

<xref:System.Int32>\
目前資料流的新位置。

## <a name="remarks"></a>備註

> [!WARNING]
> @No__t-0 方法是私用的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**元件：** System.web （在 System.web 中）

**.NET Framework 版本：** 自2.0 開始提供。
