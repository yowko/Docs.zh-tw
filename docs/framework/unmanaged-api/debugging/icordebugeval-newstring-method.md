---
title: ICorDebugEval::NewString 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50a18f435063b74b837dbfe9e4f1d986bb735039
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753350"
---
# <a name="icordebugevalnewstring-method"></a>ICorDebugEval::NewString 方法
會配置新的字串執行個體具有指定的內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a>參數  
 `string`  
 [in]字串內容的指標。  
  
## <a name="remarks"></a>備註  
 字串一律會建立目前執行所在之執行緒的應用程式定義域中。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
