---
title: "ICorDebugRegisterSet2::GetRegisters 方法"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 830fd9b4c04d536f64ca5b15e513c9f5f049f059
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters 方法
取得每個暫存器值 （適用於目前執行所在的程式碼的平台） 所指定的位元遮罩指定。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `maskCount`  
 [in]大小，以位元組為單位的`mask`陣列。  
  
 `mask`  
 [in]位元組陣列，其中每個位元對應暫存器。 如果位元為 1，將會擷取對應的暫存值。  
  
 `regCount`  
 [in]要擷取的暫存器值數目。  
  
 `regBuffer`  
 [out]陣列`CORDB_REGISTER`物件，其中每個收到的暫存器值。  
  
## <a name="remarks"></a>備註  
 `GetRegisters`方法會傳回值的陣列，從遮罩所指定的暫存器。 陣列未包含未設定遮罩位元暫存器值。 因此，大小`regBuffer`陣列必須有等於遮罩中的 1 的數目。 如果值`regCount`是太小會從集合中截斷的遮罩，較高編號的暫存器的值所表示的暫存器數目。 如果`regCount`太大，未使用`regBuffer`項目就是未修改。  
  
 如果無法使用的暫存器遮罩所指示，該暫存器將傳回的不定值。  
  
 `ICorDebugRegisterSet2::GetRegisters`方法是必要的平台具有 64 個以上的暫存器。 例如，IA64 具有 128 一般用途的暫存器和 128 浮點暫存器，因此您需要多個 64 位元的位元遮罩中。  
  
 如果在此情況下，在 x86、 平台上的不具有 64 個以上的暫存器`GetRegisters`方法實際上只會轉譯中的位元組`mask`到位元組陣列`ULONG64`，然後呼叫[ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)方法會採用`ULONG64`遮罩。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorDebugRegisterSet2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [ICorDebugRegisterSet 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
