---
title: 服務點管理器.s_ServicePointTable欄位
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
ms.openlocfilehash: 6a56ecd6fc85005f5987c3c2ad0d1680ca63c398
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155805"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>服務點管理器的服務\_點表字段

`ServicePointManager.s_ServicePointTable`是<xref:System.Collections.Hashtable>包含 中的活動 HTTP 連接的清單<xref:System.Net.ServicePoint>的<xref:System.AppDomain>。

## <a name="syntax"></a>語法
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> 該`ServicePointManager.s_ServicePointTable`欄位是私有的，不應直接用於代碼。
>
> 在任何情況下，Microsoft 都不支援在生產應用程式中使用此欄位。

## <a name="requirements"></a>需求

**命名空間：**<xref:System.Net>

**裝配：** 系統（系統中）

**.NET 框架版本：** 自 2.0 起可用。
