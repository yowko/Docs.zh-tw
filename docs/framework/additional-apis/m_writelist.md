---
title: 連接.m_WriteList欄位
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
ms.openlocfilehash: 6c60831ddf23ce8ac9afcf244383d24732c3ef8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155833"
---
# <a name="connectionm_writelist-field"></a>連接.m\_寫入清單欄位

`Connection.m_WriteList`<xref:System.Collections.ArrayList>是排隊通過<xref:System.Net.HttpWebRequest>HTTP 發送的物件。

## <a name="syntax"></a>語法
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> 該`Connection.m_WriteList`欄位是私有的，不應直接用於代碼。
>
> 在任何情況下，Microsoft 都不支援在生產應用程式中使用此欄位。

## <a name="requirements"></a>需求

**命名空間：**<xref:System.Net>

**裝配：** 系統（系統中）

**.NET 框架版本：** 自 2.0 起可用。
