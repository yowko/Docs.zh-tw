---
title: ICorDebugCode 介面 1
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
ms.openlocfilehash: db2fe1e854069d9b5d566fc00420615e0c06b3d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575943"
---
# <a name="icordebugcode-interface1"></a>ICorDebugCode 介面 1
表示 Microsoft Intermediate Language (MSIL) 程式碼或機器碼的區段。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|建立指定之位移的中斷點。|  
|[GetAddress 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|取得程式碼片段的相對虛擬位址 (RVA)，這`ICorDebugCode`表示。|  
|[GetCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|取得指定的函式，針對 反組譯碼格式化的所有程式碼。 此方法已被取代;使用  [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)改。|  
|[GetEnCRemapSequencePoints 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|未實作。|  
|[GetFunction 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|取得與此相關聯 「 ICorDebugFunction" `ICorDebugCode`。|  
|[GetILToNativeMapping 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|取得"COR_DEBUG_IL_TO_NATIVE_MAP 」 執行個體，表示對應的 MSIL 位移到原生位移陣列。|  
|[GetSize 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|取得以位元組為單位所表示的二進位程式碼的大小， `ICorDebugCode`。|  
|[GetVersionNumber 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|取得以一為基的數字的程式碼版本識別這個`ICorDebugCode`表示。|  
|[IsIL 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|取得值，指出是否此`ICorDebugCode`編譯的 MSIL。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugCode` 可以表示 MSIL 或原生程式碼。 表示 MSIL 程式碼的 「 ICorDebugFunction"物件可以有零個或一個`ICorDebugCode`與其相關聯的物件。 表示原生程式碼的 「 ICorDebugFunction"物件可以有任意數目的`ICorDebugCode`與其相關聯的物件。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugCode3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
