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
ms.openlocfilehash: 71b9d59621efb547713cb4a6c9df7a7142f4a677
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615185"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2：： GetRegisters 方法

取得給定位元遮罩所指定之每個暫存器的值（適用于目前執行程式碼的平臺）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>參數

 `maskCount`  
 在陣列的大小（以位元組為單位） `mask` 。  
  
 `mask`  
 在位元組陣列，其中每個位對應至暫存器。 如果位為1，則會抓取對應的暫存器值。  
  
 `regCount`  
 在要抓取的暫存器值數目。  
  
 `regBuffer`  
 脫銷物件的陣列 `CORDB_REGISTER` ，其中每一個都會接收暫存器的值。  
  
## <a name="remarks"></a>備註

 `GetRegisters`方法會從遮罩所指定的暫存器中傳回值的陣列。 陣列不包含未設定其 mask 位的暫存器值。 因此，陣列的大小 `regBuffer` 必須等於遮罩中的1。 如果的值 `regCount` 太小，用於遮罩所指示的暫存器數目，則較高編號的暫存器值將會從集合中截斷。 如果 `regCount` 太大，則不會修改未使用的 `regBuffer` 元素。  
  
 如果遮罩會指出無法使用的暫存器，則會傳回該暫存器的不定值。  
  
 在具有超過64暫存器的平臺中，此 `ICorDebugRegisterSet2::GetRegisters` 方法是必要的。 例如，IA64 具有128一般用途暫存器和128浮點暫存器，因此您在位元遮罩中需要超過64個位。  
  
 如果您沒有超過64暫存器（如 x86 之類的平臺）， `GetRegisters` 方法只會將位元組陣列中的位元組轉譯 `mask` 成 `ULONG64` ，然後呼叫[ICorDebugRegisterSet：： GetRegisters](icordebugregisterset-getregisters-method.md)方法，它會採用 `ULONG64` 遮罩。  
  
## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugRegisterSet2 介面](icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet 介面](icordebugregisterset-interface.md)
