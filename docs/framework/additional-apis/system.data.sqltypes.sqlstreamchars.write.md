---
title: SqlStreamChars.Write (Char []，Int32，Int32) 方法 (System.Data.SqlTypes)
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
ms.openlocfilehash: 4084c7161eaa91d78eab32f1c14624e0032cdfcf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705905"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a>SqlStreamChars.Write (Char []，Int32，Int32) 方法

當在衍生類別中覆寫時，寫入目前資料流的字元序列，這個資料流中的目前位置前移寫入的字元數。 包含這個方法的組件有 SQLAccess.dll friend 關聯性。 它適用於 SQL server。 其他資料庫，請使用該資料庫所提供的主控機制。

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>參數

`buffer`  
要寫入的字元陣列。

`offset`  
相對於原點的位移。

`count`  
要寫入目前資料流的字元數。

## <a name="remarks"></a>備註

> [!WARNING]
> `SqlStreamChars.Write`方法是私用，而且不適合直接在您的程式碼中使用。
>
> Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**組件：** System.Data （在 System.Data.dll 中)

**.NET framework 版本：** 自 2.0 起可用。
