---
title: SqlStreamChars.Flush 方法 (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ecaf7932a4e832a88b883ceac4746afe6140b38e
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152741"
---
# <a name="sqlstreamcharsflush-method"></a>SqlStreamChars.Flush 方法

當在衍生類別中覆寫時，會清除這個資料流的所有緩衝區，並造成所有緩衝資料都寫入基礎裝置。 包含這個方法的組件有 SQLAccess.dll friend 關聯性。 它適用於 SQL server。 其他資料庫，請使用該資料庫所提供的主控機制。

## <a name="syntax"></a>語法

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a>備註

> [!WARNING]
> `SqlStreamChars.Flush`方法是私用，而且不適合直接在您的程式碼中使用。
>
> Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**組件：** System.Data （在 System.Data.dll 中)

**.NET framework 版本：** 自 2.0 起可用。