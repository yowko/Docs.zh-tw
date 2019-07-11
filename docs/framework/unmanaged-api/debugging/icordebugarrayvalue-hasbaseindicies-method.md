---
title: ICorDebugArrayValue::HasBaseIndicies 方法
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c488ca3a77f2c2b2a40c6143989cd86adf071787
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737426"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a>ICorDebugArrayValue::HasBaseIndicies 方法
取得值，指出這個陣列的任何維度是否具有非零的基底索引。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbHasBaseIndicies`  
 [out]布林值的指標`true`如果這個的一或多個維度`ICorDebugArrayValue`物件的基底的索引為非零; 否則布林值是`false`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]
