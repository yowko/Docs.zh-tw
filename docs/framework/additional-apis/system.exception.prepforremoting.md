---
title: PrepForRemoting 方法（系統）
description: 請參閱 .NET 中的 PrepForRemoting 方法。 方法會在用戶端重新擲回例外狀況之前，將伺服器端堆疊追蹤加入至訊息。
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 9ceb73499ae3bb308975e6db5b961bfe40165ba3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105264"
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
> `Exception.PrepForRemoting`方法是內部的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。

## <a name="requirements"></a>需求

**命名空間：** <xref:System>

**元件：** mscorlib.dll （在 mscorlib.dll 中）

**.NET Framework 版本：** 自1.0 開始提供。
