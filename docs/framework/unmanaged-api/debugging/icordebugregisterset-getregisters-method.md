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
ms.openlocfilehash: 315e4cc3b93fc78e11a4fb399bbe6f8a9f55ac84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705003"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters 方法

取得電腦上每個登錄 (的值，此電腦上目前正在執行位元遮罩所指定的程式碼) 。  
  
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
 在位元遮罩，指定要取出的暫存器值。 每個位都對應到一個暫存器。 如果位設定為1，則會抓取登錄的值;否則，就不會抓取暫存器的值。  
  
 `regCount`  
 在要取出的暫存器值數目。  
  
 `regBuffer`  
 擴展物件的陣列 `CORDB_REGISTER` ，每個物件都會收到一個暫存器值。  
  
## <a name="remarks"></a>備註  

 陣列的大小應等於位元遮罩中設定為1的位數。 `regCount`參數會指定緩衝區中將接收暫存器值的元素數目。 如果 `regCount` 值對遮罩所指示的暫存器數量而言太小，則會從集合中截斷較高編號的暫存器。 如果 `regCount` 值太大，則 `regBuffer` 不會修改未使用的元素。  
  
 如果位元遮罩指定的登錄無法使用，則會傳回該暫存器的 `GetRegisters` 不定值。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugRegisterSet 介面](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 介面](icordebugregisterset2-interface.md)
