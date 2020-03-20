---
title: ICorDebugRegisterSet::GetRegisters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 32e899622b9c649a08e3bca1b6645f70dcbcbb19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178537"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters 方法
獲取位元遮罩指定的每個寄存器的值（當前正在執行代碼的電腦）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `mask`  
 [在]指定要檢索哪些寄存器值的位元遮罩。 每個位對應于寄存器。 如果位設置為 1，則檢索寄存器的值;如果位設置為 1，則檢索寄存器的值。否則，不會檢索寄存器的值。  
  
 `regCount`  
 [在]要檢索的寄存器值數。  
  
 `regBuffer`  
 [出]物件陣列`CORDB_REGISTER`，每個物件都接收寄存器的值。  
  
## <a name="remarks"></a>備註  
 陣列的大小應等於位元遮罩中設置為 1 的位數。 參數`regCount`指定將接收寄存器值的緩衝區中的元素數。 如果`regCount`該值對於遮罩指示的寄存器數太小，則較高的編號寄存器將從集中截斷。 如果`regCount`該值太大，則未使用`regBuffer`的元素將取消修改。  
  
 如果位元遮罩指定不可用的寄存器，`GetRegisters`則返回該寄存器的不確定值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugRegisterSet 介面](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 介面](icordebugregisterset2-interface.md)
