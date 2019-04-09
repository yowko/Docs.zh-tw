---
title: ICorDebugRegisterSet2::GetRegisters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2dc1064656f3493db78d858cf1e86db0cb83d6c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136691"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters 方法
取得每個暫存器值 （適用於目前執行所在的程式碼的平台） 所指定的特定位元遮罩。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `maskCount`  
 [in]大小，以位元組為單位的`mask`陣列。  
  
 `mask`  
 [in]位元組陣列，其中每個位元對應暫存器。 如果位元為 1，將會擷取對應的暫存器值。  
  
 `regCount`  
 [in]要擷取的暫存器值數目。  
  
 `regBuffer`  
 [out]陣列`CORDB_REGISTER`物件，其中每個收到的暫存器值。  
  
## <a name="remarks"></a>備註  
 `GetRegisters`方法會從遮罩所指定的暫存器傳回值的陣列。 陣列未包含暫存器未設定位元的遮罩的值。 因此，大小`regBuffer`必須等於遮罩中數字 1 的陣列。 如果值`regCount`為太小會從集合中截斷的遮罩，較高編號的暫存器的值所表示的暫存器數目。 如果`regCount`太大，未使用`regBuffer`項目將會是未修改。  
  
 如果無法使用的暫存器由遮罩，就會傳回不定值的一個該暫存器。  
  
 `ICorDebugRegisterSet2::GetRegisters`方法是必要的平台具有 64 個以上的暫存器。 比方說，IA64 有 128 一般用途的暫存器和 128 的浮點數暫存器，因此您需要更大 64 位元的位元遮罩中。  
  
 如果您不需要 64 個以上的暫存器，在此情況下，例如 x86 平台上的`GetRegisters`方法實際上只會轉譯中的位元組`mask`位元組陣列`ULONG64`，然後呼叫[ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)方法，後者會採用`ULONG64`遮罩。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugRegisterSet2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
