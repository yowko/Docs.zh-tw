---
title: SqlStreamChars.Seek （Int64，SeekOrigin） 方法 (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: aab3195ec0d300a7f001f98f2d646c85be939356
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152551"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a>SqlStreamChars.Seek （Int64，SeekOrigin） 方法

在衍生類別中覆寫時，設定在目前資料流的位置。 包含這個方法的組件有 SQLAccess.dll friend 關聯性。 它適用於 SQL server。 其他資料庫，請使用該資料庫所提供的主控機制。

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a>參數

`offset`\
位元組位移，相對於`origin`。

`origin`\
其中一個列舉值，指出要從中取得新位置的參考點。

## <a name="returns"></a>Returns

<xref:System.Int32>\
目前資料流的新位置。

## <a name="remarks"></a>備註

> [!WARNING]
> `SqlStreamChars.Seek`方法是私用，而且不適合直接在您的程式碼中使用。
>
> Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**組件：** System.Data （在 System.Data.dll 中)

**.NET framework 版本：** 自 2.0 起可用。