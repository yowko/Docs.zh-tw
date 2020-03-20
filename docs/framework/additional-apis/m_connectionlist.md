---
title: 連接組.m_ConnectionList欄位
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
ms.openlocfilehash: 8eb6f215c36e214f7095eeba90bf0aed66dfcea0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155846"
---
# <a name="connectiongroupm_connectionlist-field"></a>連接組.m\_連接清單欄位

`ConnectionGroup.m_ConnectionList`是一<xref:System.Collections.ArrayList>個連線物件，用於相同的 URI，並為某些其他屬性（如過期和身份驗證）共用相同的值。

## <a name="syntax"></a>語法
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> 該`ConnectionGroup.m_ConnectionList`欄位是私有的，不應直接用於代碼。
>
> 在任何情況下，Microsoft 都不支援在生產應用程式中使用此欄位。

## <a name="requirements"></a>需求

**命名空間：**<xref:System.Net>

**裝配：** 系統（系統中）

**.NET 框架版本：** 自 2.0 起可用。
