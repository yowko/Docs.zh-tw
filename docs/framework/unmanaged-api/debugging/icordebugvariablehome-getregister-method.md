---
title: ICorDebugVariableHome：： GetRegister 方法
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
ms.openlocfilehash: 6cf66774209bd07426872c29c15b2225421c2b4d
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396825"
---
# <a name="icordebugvariablehomegetregister-method"></a>ICorDebugVariableHome：： GetRegister 方法
取得包含位置類型為之變數的暫存器 `VLT_REGISTER` ，以及位置類型為之變數的基底暫存器 `VLT_REGISTER_RELATIVE` 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a>參數  
 `pRegister`  
 脫銷CorDebugRegister 列舉值，指出位置類型為之變數的暫存器 `VLT_REGISTER` ，以及位置類型為之變數的基底暫存器 `VLT_REGISTER_RELATIVE` 。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回下列值：  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|變數位於引數所指示的暫存器中 `pRegister` 。|  
|`E_FAIL`|變數不在暫存器或暫存器相對位置。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [VariableLocationType 列舉](variablelocationtype-enumeration.md)
- [ICorDebugVariableHome 介面](icordebugvariablehome-interface.md)
