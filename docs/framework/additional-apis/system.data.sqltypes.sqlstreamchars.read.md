---
title: SqlStreamChars.Read (Char []，Int32，Int32) 方法 (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 87bff6dd78743ae08a5a3db8a783b56a0b7c3f24
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152531"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a>SqlStreamChars.Read (Char []，Int32，Int32) 方法

當在衍生類別中覆寫時，請從輸入資料流讀取下的一組字元。 包含這個方法的組件有 SQLAccess.dll friend 關聯性。 它適用於 SQL server。 其他資料庫，請使用該資料庫所提供的主控機制。

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>參數

`buffer`\
要讀取的字元陣列。

`offset`\
相對於原點的位移。

`count`\
若要從目前資料流讀取的字元數。

## <a name="returns"></a>Returns

<xref:System.Int32>\
讀入緩衝區的字元總數。

## <a name="remarks"></a>備註

> [!WARNING]
> `SqlStreamChars.Read`方法是私用，而且不適合直接在您的程式碼中使用。
>
> Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**組件：** System.Data （在 System.Data.dll 中)

**.NET framework 版本：** 自 2.0 起可用。