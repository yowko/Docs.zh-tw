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
ms.openlocfilehash: 03cbc1a598ba6c0166f72ff404c239763956c996
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687602"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode 介面

表示 Microsoft Intermediate Language (MSIL) 程式碼或機器碼的區段。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](icordebugcode-createbreakpoint-method.md)|在指定的位移處建立中斷點。|  
|[GetAddress 方法](icordebugcode-getaddress-method.md)|取得這個所代表之程式碼區段 (RVA) 的相對虛擬位址 `ICorDebugCode` 。|  
|[GetCode 方法](icordebugcode-getcode-method.md)|取得指定之函式的所有程式碼，並針對反組解碼進行格式化。 這個方法已被取代;請改用 [ICorDebugCode2：： GetCodeChunks](icordebugcode2-getcodechunks-method.md) 。|  
|[GetEnCRemapSequencePoints 方法](icordebugcode-getencremapsequencepoints-method.md)|未實作。|  
|[GetFunction 方法](icordebugcode-getfunction-method.md)|取得與此相關聯的 "ICorDebugFunction" `ICorDebugCode` 。|  
|[GetILToNativeMapping 方法](icordebugcode-getiltonativemapping-method.md)|取得 "COR_DEBUG_IL_TO_NATIVE_MAP" 實例的陣列，這些實例表示從 MSIL 位移到原生位移的對應。|  
|[GetSize 方法](icordebugcode-getsize-method.md)|取得這個所表示之二進位程式碼的大小（以位元組為單位） `ICorDebugCode` 。|  
|[GetVersionNumber 方法](icordebugcode-getversionnumber-method.md)|取得以一為基礎的數位，識別此所代表的程式碼版本 `ICorDebugCode` 。|  
|[IsIL 方法](icordebugcode-isil-method.md)|取得值，這個值會指出這個是否 `ICorDebugCode` 會在 MSIL 中進行編譯。|  
  
## <a name="remarks"></a>備註  

 `ICorDebugCode` 可以代表 MSIL 或機器碼。 代表 MSIL 程式碼的 "ICorDebugFunction" 物件可以有零個或一個 `ICorDebugCode` 與其相關聯的物件。 代表原生程式碼的 "ICorDebugFunction" 物件可以有任意數目的 `ICorDebugCode` 物件與其相關聯。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugCode3 介面](icordebugcode3-interface.md)
- [偵錯介面](debugging-interfaces.md)
