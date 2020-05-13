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
ms.openlocfilehash: 40de06d47654337542d2c80dc325f8201335312a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379146"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters 方法
取得位元遮罩所指定之每個暫存器（目前執行程式碼的電腦）的值。  
  
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
 在位元遮罩，指定要抓取的暫存器值。 每個位都會對應到一個暫存器。 如果位設為1，則會抓取暫存器的值;否則，就不會抓取暫存器的值。  
  
 `regCount`  
 在要抓取的暫存器值數目。  
  
 `regBuffer`  
 脫銷物件的陣列 `CORDB_REGISTER` ，其中每一個都會接收暫存器的值。  
  
## <a name="remarks"></a>備註  
 陣列的大小應該等於位元遮罩中設定為一個的位數。 `regCount`參數會指定要接收暫存器值之緩衝區中的元素數目。 如果此 `regCount` 值對遮罩所指示的暫存器數目而言太小，則會從集合中截斷較高編號的暫存器。 如果 `regCount` 值太大，則 `regBuffer` 不會修改未使用的元素。  
  
 如果位元遮罩指定無法使用的暫存器，則會傳回該暫存器的 `GetRegisters` 不定值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugRegisterSet 介面](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 介面](icordebugregisterset2-interface.md)
