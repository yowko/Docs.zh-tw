---
title: PrepForRemoting 方法（系統）
author: mairaw
ms.author: mairaw
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 057390d64f70d3cb8eba7d4b29b94570fdca77e3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72405029"
---
# <a name="exceptionprepforremoting-method"></a>PrepForRemoting 方法

保留伺服器端堆疊追蹤，方法是將它附加至訊息，然後在用戶端呼叫網站重新擲回例外狀況。

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Returns

<xref:System.Exception>  
這個 <xref:System.Exception> 執行個體。

## <a name="remarks"></a>備註

> [!WARNING]
> @No__t-0 方法是內部的，而且不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System>

**元件：** mscorlib （在 mscorlib.dll 中）

**.NET Framework 版本：** 自1.0 開始提供。
