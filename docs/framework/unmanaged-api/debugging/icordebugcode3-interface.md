---
title: ICorDebugCode3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
ms.openlocfilehash: f2f75c3c54c0fa2d55dc0179c05e4edea6e36738
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777820"
---
# <a name="icordebugcode3-interface"></a>ICorDebugCode3 介面
提供擴充 "ICorDebugCode" 和 "ICorDebugCode2" 的方法，以提供受控傳回值的相關資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReturnValueLiveOffset 方法](icordebugcode3-getreturnvalueliveoffset-method.md)|針對指定的 IL 位移，取得應放置中斷點的原生位移，讓偵錯工具可以從函數取得傳回值。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugILFrame3 介面](icordebugilframe3-interface.md)
- [偵錯介面](debugging-interfaces.md)
