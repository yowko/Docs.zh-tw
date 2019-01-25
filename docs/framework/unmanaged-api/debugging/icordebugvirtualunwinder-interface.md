---
title: ICorDebugVirtualUnwinder 介面
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9db6b83e2feedd761b95dec455213051e37366e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684141"
---
# <a name="icordebugvirtualunwinder-interface"></a>ICorDebugVirtualUnwinder 介面
提供可協助堆疊回溯的方法。  
  
## <a name="methods"></a>方法  
  
|方法|名稱|  
|------------|----------|  
|[GetContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|取得此回溯器的目前內容。|  
|[Next 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|進入呼叫端的內容。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugVirtualUnwinder` 介面的成員由偵錯工具實作，協助堆疊回溯。  
  
> [!NOTE]
>  這個介面僅適用於 .NET 原生。 如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
