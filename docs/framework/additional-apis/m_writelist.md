---
title: 連接。 m_WriteList 欄位
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
ms.openlocfilehash: 22f939d13cceac4d1c0b39e9e8fe20cdc0ab9387
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214907"
---
# <a name="connectionm_writelist-field"></a>連接. m\_WriteList 欄位

`Connection.m_WriteList` 是已排入佇列以透過 HTTP 傳送之 <xref:System.Net.HttpWebRequest> 物件的 <xref:System.Collections.ArrayList>。

## <a name="syntax"></a>語法
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> [`Connection.m_WriteList`] 欄位是私用的，不適合直接在程式碼中使用。
> 
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此欄位。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System .dll 中）

**.NET Framework 版本：** 自2.0 開始提供。
