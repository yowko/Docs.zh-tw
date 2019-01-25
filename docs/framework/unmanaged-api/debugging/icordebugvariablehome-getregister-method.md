---
title: ICorDebugVariableHome::GetRegister 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d678b6f52719287a1e8bbe88d178fa47b2893ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563141"
---
# <a name="icordebugvariablehomegetregister-method"></a>ICorDebugVariableHome::GetRegister 方法
取得包含位置類型的變數的暫存`VLT_REGISTER`，及基底的位置類型的變數報名`VLT_REGISTER_RELATIVE`。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRegister`  
 [out]CorDebugRegister 列舉值，指出的位置類型的變數報名`VLT_REGISTER`，及基底的位置類型的變數報名`VLT_REGISTER_RELATIVE`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回下列值：  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|變數是在暫存器中所指示`pRegister`引數。|  
|`E_FAIL`|變數不是在暫存器或暫存器的相對位置。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [VariableLocationType 列舉](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [ICorDebugVariableHome 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
