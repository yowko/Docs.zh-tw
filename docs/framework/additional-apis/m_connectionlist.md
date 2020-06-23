---
title: ConnectionGroup。 m_ConnectionList] 欄位
description: 瞭解 .NET 中的 m_ConnectionList ConnectionGroup 欄位，其中包含可為其他屬性提供相同 URI 和共用值的連線物件。
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup.m_ConnectionList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 186083cf-8dff-4600-a2ab-6fed4b4de6af
ms.openlocfilehash: 478b2441c062e8df6f4e718bd66d7af329f20f12
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989719"
---
# <a name="connectiongroupm_connectionlist-field"></a>ConnectionGroup. m \_ ConnectionList 欄位

`ConnectionGroup.m_ConnectionList`是 <xref:System.Collections.ArrayList> 連線物件的，它會提供相同的 URI，並針對某些其他屬性（例如到期和驗證）共用相同的值。

## <a name="syntax"></a>Syntax
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> `ConnectionGroup.m_ConnectionList`欄位是私用的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此欄位。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System.dll 中）

**.NET Framework 版本：** 自2.0 開始提供。
