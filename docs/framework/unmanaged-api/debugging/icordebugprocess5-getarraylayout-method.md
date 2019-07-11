---
title: ICorDebugProcess5::GetArrayLayout 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1afb87e063a18bd05bedf856f8b7ebdf0e47e91
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767428"
---
# <a name="icordebugprocess5getarraylayout-method"></a>ICorDebugProcess5::GetArrayLayout 方法
提供關於版面配置的陣列類型的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a>參數  
 `id`  
 [in]A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)語彙基元，指定想要使用的配置的陣列。  
  
 `pLayout`  
 [out]指標[COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)結構，包含在記憶體中陣列的版面配置的相關資訊。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess5 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
