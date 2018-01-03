---
title: "ICorDebugRegisterSet::GetRegisters 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ddefb1ac5694bf1f213dd77e0ffc7f746b7e62cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters 方法
取得每個暫存器值 （在電腦上目前正在執行的程式碼） 的位元遮罩所指定。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `mask`  
 [in]位元遮罩，指定的值為要擷取哪一個暫存器。 每個位元對應暫存器。 如果一個位元設定為其中一個，擷取暫存器的值;否則，不會擷取暫存器的值。  
  
 `regCount`  
 [in]要擷取的暫存器值數目。  
  
 `regBuffer`  
 [out]陣列`CORDB_REGISTER`物件，其中每個收到的暫存器的值。  
  
## <a name="remarks"></a>備註  
 陣列的大小應該會等於設為其中一個位元遮罩中的位元數。 `regCount`參數緩衝區將會接收暫存器值中指定的項目數。 如果`regCount`值是由遮罩所指示的暫存器數目太小，較高編號的暫存器會從集合中截斷。 如果`regCount`值太大，而未使用`regBuffer`項目就是未修改。  
  
 如果位元遮罩指定的暫存器無法使用，`GetRegisters`傳回該暫存器的不定值。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorDebugRegisterSet 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [ICorDebugRegisterSet2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
