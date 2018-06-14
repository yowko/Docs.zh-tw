---
title: ServicePointManager.s_ServicePointTable 欄位
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
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 5450a0cb3e5bd39a86365b16d372c7e573a43496
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351754"
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable 欄位

`ServicePointManager.s_ServicePointTable` 是<xref:System.Collections.Hashtable>包含使用中的 HTTP 連接的清單 (<xref:System.Net.ServicePoint>s) 中<xref:System.AppDomain>。

## <a name="syntax"></a>語法
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable`欄位是私用，而且不會直接在您的程式碼中使用它們。
> 
> Microsoft 不支援在實際執行應用程式在任何情況下使用此欄位。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**組件：** 系統 （在 System.dll)

**.NET framework 版本：** 自 2.0 起可用。
