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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b417685361126951470571e2440cc842ab1c94fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153903"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters 方法
取得每個暫存器值 （在電腦上目前正在執行的程式碼） 所指定的位元遮罩。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `mask`  
 [in]位元遮罩，指定要擷取的值為哪一個暫存器。 每個位元對應暫存器。 如果位元設定為其中一個，就會擷取暫存器的值;否則，不會擷取暫存器的值。  
  
 `regCount`  
 [in]要擷取的暫存器值數目。  
  
 `regBuffer`  
 [out]陣列`CORDB_REGISTER`物件，其中每個收到的暫存器值。  
  
## <a name="remarks"></a>備註  
 陣列的大小應該是等於設為其中一個位元遮罩中的位元數。 `regCount`參數將會收到暫存器值之緩衝區中指定的項目數。 如果`regCount`值遮罩所表示的暫存器數目太小，較高編號的暫存器會從集合中截斷。 如果`regCount`值太大，而未使用`regBuffer`項目將會是未修改。  
  
 如果位元遮罩指定的暫存器無法使用，`GetRegisters`傳回不定值，該暫存器。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugRegisterSet 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
