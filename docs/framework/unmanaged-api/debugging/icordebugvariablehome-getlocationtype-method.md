---
title: ICorDebugVariableHome::GetLocationType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b7b95c79b41737ade42e6a9a2741f9c43a41130
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774462"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a>ICorDebugVariableHome::GetLocationType 方法
取得變數的原生位置類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a>參數  
 `pLocationType`  
 [out]變數的原生位置的類型指標。  請參閱[VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)列舉型別，如需詳細資訊。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugVariableHome 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [VariableLocationType 列舉](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
