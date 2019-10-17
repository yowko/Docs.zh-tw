---
title: SqlStreamChars. Write （Char []，Int32，Int32）方法（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9d952041122ceb3824712bd81cab7ce4789c9db8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395580"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a>SqlStreamChars. Write （Char []，Int32，Int32）方法

在衍生類別中覆寫時，將一連串的字元寫入目前的資料流程，並將此資料流程中目前的位置前移寫入的字元數。 包含這個方法的元件與 SQLAccess 具有 friend 關聯性。 其目的是要供 SQL Server 使用。 若為其他資料庫，請使用該資料庫所提供的裝載機制。

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>參數

`buffer`  
要寫入的字元陣列。

`offset`  
相對於原點的位移。

`count`  
要寫入目前資料流程的字元數。

## <a name="remarks"></a>備註

> [!WARNING]
> @No__t-0 方法是私用的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援使用此方法在生產應用程式中寫入。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**元件：** System.web （在 System.web 中）

**.NET Framework 版本：** 自2.0 開始提供。
