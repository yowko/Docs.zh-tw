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
ms.openlocfilehash: 396dd9c017fca6dc7037b43355ba7f726d7390ea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790981"
---
# <a name="icordebugvariablehomegetregister-method"></a>ICorDebugVariableHome：： GetRegister 方法
取得包含 `VLT_REGISTER`之位置類型之變數的暫存器，以及具有 `VLT_REGISTER_RELATIVE`位置類型之變數的基底暫存器。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a>參數  
 `pRegister`  
 脫銷CorDebugRegister 列舉值，指出位置類型為 `VLT_REGISTER`之變數的暫存器，以及位置類型為 `VLT_REGISTER_RELATIVE`之變數的基底暫存器。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回下列值：  
  
|{2&gt;值&lt;2}|描述|  
|-----------|-----------------|  
|`S_OK`|變數位於 `pRegister` 引數所指示的暫存器中。|  
|`E_FAIL`|變數不在暫存器或暫存器相對位置。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [VariableLocationType 列舉](variablelocationtype-enumeration.md)
- [ICorDebugVariableHome 介面](icordebugvariablehome-interface.md)
