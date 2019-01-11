---
title: SqlChars.Stream 屬性 (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d756b78a7cdbc12562e474ca3d2c9a1f3529f6bf
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223048"
---
# <a name="sqlcharsstream-property"></a>SqlChars.Stream 屬性

取得或設定字元資料流。 包含此屬性的組件有 SQLAccess.dll friend 關聯性。 它適用於 SQL server。 其他資料庫，請使用該資料庫所提供的主控機制。

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a>屬性值

`System.Data.SqlTypes.SqlStreamChars`\
字元資料流中。

## <a name="remarks"></a>備註

> [!WARNING]
> `SqlChars.Stream`屬性內部，且不適合直接在您的程式碼中使用。
>
> 在生產環境應用程式中任何情況下，Microsoft 不支援這個屬性的使用。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**組件：** System.Data （在 System.Data.dll 中)

**.NET framework 版本：** 自 2.0 起可用。