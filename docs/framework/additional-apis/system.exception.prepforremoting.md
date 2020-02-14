---
title: PrepForRemoting 方法（系統）
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: ce1c24578690a1643b7f5af0e44eaae95ed7b0a2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214891"
---
# <a name="exceptionprepforremoting-method"></a>Exception.PrepForRemoting 方法

保留伺服器端堆疊追蹤，方法是將它附加至訊息，然後在用戶端呼叫網站重新擲回例外狀況。

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>傳回值

<xref:System.Exception>  
這個 <xref:System.Exception> 執行個體。

## <a name="remarks"></a>備註

> [!WARNING]
> `Exception.PrepForRemoting` 方法是內部的，而且不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。

## <a name="requirements"></a>需求

**命名空間：** <xref:System>

**元件：** mscorlib （在 mscorlib.dll 中）

**.NET Framework 版本：** 自1.0 開始提供。
