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
ms.openlocfilehash: ebcf5c3f13b3bd30a8e091be09ae546eee1eaffe
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147443"
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable 欄位

`ServicePointManager.s_ServicePointTable` 已<xref:System.Collections.Hashtable>，其中包含作用中的 HTTP 連接的清單 (<xref:System.Net.ServicePoint>s) 中<xref:System.AppDomain>。

## <a name="syntax"></a>語法
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable`欄位是私用，而不是直接在您的程式碼中使用。
> 
> Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Net>

**組件：**（在 System.dll) 的系統

**.NET framework 版本：** 自 2.0 起可用。
