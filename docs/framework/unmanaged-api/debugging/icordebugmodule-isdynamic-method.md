---
title: ICorDebugModule::IsDynamic 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
ms.openlocfilehash: 45b1d0c0a3199227ab644ba8732198dd14b1cb4c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793001"
---
# <a name="icordebugmoduleisdynamic-method"></a>ICorDebugModule::IsDynamic 方法
取得值，指出此模組是否為動態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a>參數  
 `pDynamic`  
 [out] `true` 如果這個模組是動態的，否則，`false`。  
  
## <a name="remarks"></a>備註  
 即使在載入模組之後，動態模組也可以加入新的類別，並刪除現有的類別。 [ICorDebugManagedCallback：： LoadClass](icordebugmanagedcallback-loadclass-method.md)和[ICorDebugManagedCallback：： UnloadClass](icordebugmanagedcallback-unloadclass-method.md)回呼會在新增或刪除類別時，通知偵錯工具。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
