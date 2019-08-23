---
title: ICorDebugCode 介面
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75cc8ea9d88dda42362f50b519864b1a78e1a64b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960797"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode 介面

表示 Microsoft Intermediate Language (MSIL) 程式碼或機器碼的區段。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[CreateBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|在指定的位移處建立中斷點。|  
|[GetAddress 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|取得這個`ICorDebugCode`所表示之程式碼區段的相對虛擬位址 (RVA)。|  
|[GetCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|取得指定函式的所有程式碼, 格式化為可進行反組譯。 這個方法已被取代。請改用[ICorDebugCode2:: GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) 。|  
|[GetEnCRemapSequencePoints 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|未實作。|  
|[GetFunction 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|取得與這個`ICorDebugCode`相關聯的 "ICorDebugFunction"。|  
|[GetILToNativeMapping 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|取得 "COR_DEBUG_IL_TO_NATIVE_MAP" 實例的陣列, 表示從 MSIL 位移到原生位移的對應。|  
|[GetSize 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|取得這個`ICorDebugCode`所表示之二進位代碼的大小 (以位元組為單位)。|  
|[GetVersionNumber 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|取得以1為基礎的數位, 識別這個`ICorDebugCode`所代表的程式碼版本。|  
|[IsIL 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|取得值, 指出這個`ICorDebugCode`是否在 MSIL 中進行編譯。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugCode`可以代表 MSIL 或機器碼。 代表 MSIL 程式碼的 "ICorDebugFunction" 物件可以有零個或一個`ICorDebugCode`相關聯的物件。 代表機器碼的 "ICorDebugFunction" 物件可以有任意數目的`ICorDebugCode`物件與其相關聯。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugCode3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
