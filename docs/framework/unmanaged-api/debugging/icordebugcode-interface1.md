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
ms.openlocfilehash: 3736627e7f42ad9db6699c31a0a618e993eef770
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893476"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode 介面

表示 Microsoft Intermediate Language (MSIL) 程式碼或機器碼的區段。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](icordebugcode-createbreakpoint-method.md)|在指定的位移處建立中斷點。|  
|[GetAddress 方法](icordebugcode-getaddress-method.md)|取得這個`ICorDebugCode`所表示之程式碼區段的相對虛擬位址（RVA）。|  
|[GetCode 方法](icordebugcode-getcode-method.md)|取得指定函式的所有程式碼，格式化為可進行反組譯。 這個方法已被取代。請改用[ICorDebugCode2：： GetCodeChunks](icordebugcode2-getcodechunks-method.md) 。|  
|[GetEnCRemapSequencePoints 方法](icordebugcode-getencremapsequencepoints-method.md)|未實作。|  
|[GetFunction 方法](icordebugcode-getfunction-method.md)|取得與這個`ICorDebugCode`相關聯的 "ICorDebugFunction"。|  
|[GetILToNativeMapping 方法](icordebugcode-getiltonativemapping-method.md)|取得 "COR_DEBUG_IL_TO_NATIVE_MAP" 實例的陣列，表示從 MSIL 位移到原生位移的對應。|  
|[GetSize 方法](icordebugcode-getsize-method.md)|取得這個`ICorDebugCode`所表示之二進位代碼的大小（以位元組為單位）。|  
|[GetVersionNumber 方法](icordebugcode-getversionnumber-method.md)|取得以1為基礎的數位，識別這個`ICorDebugCode`所代表的程式碼版本。|  
|[IsIL 方法](icordebugcode-isil-method.md)|取得值，指出這個`ICorDebugCode`是否在 MSIL 中進行編譯。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugCode`可以代表 MSIL 或機器碼。 代表 MSIL 程式碼的 "ICorDebugFunction" 物件可以有零個或一個`ICorDebugCode`相關聯的物件。 代表機器碼的 "ICorDebugFunction" 物件可以有任意數目的`ICorDebugCode`物件與其相關聯。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugCode3 介面](icordebugcode3-interface.md)
- [偵錯介面](debugging-interfaces.md)
