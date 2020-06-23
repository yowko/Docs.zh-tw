---
title: ServicePoint。 m_ConnectionGroupList] 欄位
description: 瞭解 m_ConnectionGroupList ServicePoint 欄位，這是連接群組的雜湊表，其中每個都會在 .NET 中保存 ServicePoint URI 的連接。
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePoint.m_ConnectionGroupList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: df8afb59-f0f6-4ddc-b3c1-839b9fc601d8
ms.openlocfilehash: 0ebfeb782147f21abfde536b8053fa15b1e1a602
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989715"
---
# <a name="servicepointm_connectiongrouplist-field"></a>ServicePoint. m \_ ConnectionGroupList 欄位

`ServicePoint.m_ConnectionGroupList`是 <xref:System.Collections.Hashtable> 連接群組的，每個都持有其 URI 的連接 <xref:System.Net.ServicePoint> 。

## <a name="syntax"></a>Syntax
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> `ServicePoint.m_ConnectionGroupList`欄位是私用的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此欄位。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System.dll 中）

**.NET Framework 版本：** 自2.0 開始提供。
