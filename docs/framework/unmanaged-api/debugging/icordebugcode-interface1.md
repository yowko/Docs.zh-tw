---
title: ICorDebugCode Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 86659b624ef01922b6c5d1db9b3ae3697d0128b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode-interface1"></a>ICorDebugCode Interface1
表示 Microsoft Intermediate Language (MSIL) 程式碼或機器碼的區段。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|建立指定之位移的中斷點。|  
|[GetAddress 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|取得程式碼片段的相對虛擬位址 (RVA)，這`ICorDebugCode`代表。|  
|[GetCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|取得指定的函式，格式為反組譯碼的所有程式碼。 這個方法已被取代。使用[icordebugcode2:: Getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)改為。|  
|[GetEnCRemapSequencePoints 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|未實作。|  
|[GetFunction 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|取得與此相關聯 「 ICorDebugFunction" `ICorDebugCode`。|  
|[GetILToNativeMapping 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|取得"COR_DEBUG_IL_TO_NATIVE_MAP 」 執行個體，以表示的 MSIL 位移的對應到原生位移的陣列。|  
|[GetSize 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|取得以位元組為單位的二進位的程式碼所代表的大小， `ICorDebugCode`。|  
|[GetVersionNumber 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|取得識別的程式碼版本 1 為基底數字這個`ICorDebugCode`代表。|  
|[IsIL 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|取得值，指出是否此`ICorDebugCode`在 MSIL 中編譯。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugCode`可以表示 MSIL 或原生程式碼。 表示 MSIL 程式碼的 「 ICorDebugFunction"物件可以有零個或一個`ICorDebugCode`與其相關聯的物件。 「 ICorDebugFunction 」 物件，表示原生程式碼可以有任意數目的`ICorDebugCode`與其相關聯的物件。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
    
 [ICorDebugCode3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
