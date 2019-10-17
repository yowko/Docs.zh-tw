---
title: SqlStreamChars. IsNull 屬性（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d80f653724b3ef0a1cadb69a5f72b1d9455597d6
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395740"
---
# <a name="sqlstreamcharsisnull-property"></a>SqlStreamChars. IsNull 屬性

在衍生類別中覆寫時，取得指出資料流程是否 `null` 的值。 包含此屬性的元件與 SQLAccess 具有 friend 關聯性。 其目的是要供 SQL Server 使用。 若為其他資料庫，請使用該資料庫所提供的裝載機制。

## <a name="syntax"></a>語法

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a>屬性值

<xref:System.Boolean>\
如果資料流程 `null`，則 `true`;否則，`false`。

## <a name="remarks"></a>備註

> [!WARNING]
> @No__t-0 屬性是私用的，而且不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此屬性。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Data.SqlTypes>

**元件：** System.web （在 System.web 中）

**.NET Framework 版本：** 自2.0 開始提供。
