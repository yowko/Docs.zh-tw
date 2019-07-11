---
title: ICorDebugAssembly2::IsFullyTrusted 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d231595ab2c7b41d1a24f654e9785b90b34ac780
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744498"
---
# <a name="icordebugassembly2isfullytrusted-method"></a>ICorDebugAssembly2::IsFullyTrusted 方法
取得值，指出是否將組件是否已授與完全信任執行階段安全性系統。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbFullyTrusted`  
 [out]`true`如果組件是否已授與完全信任執行階段安全性系統中; 否則`false`。  
  
## <a name="remarks"></a>備註  
 這個方法會傳回 HRESULT 的 CORDBG_E_NOTREADY 如果組件的安全性原則有尚未解決，亦即，如果組件中的任何程式碼尚未執行。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
