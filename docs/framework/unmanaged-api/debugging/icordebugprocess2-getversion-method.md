---
title: ICorDebugProcess2::GetVersion 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 nterface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1e1f850e85099a466c497a8fcc822bce9510f69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess2getversion-method"></a>ICorDebugProcess2::GetVersion 方法
取得 common language runtime (CLR) 執行此程序中的版本號碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetVersion (  
    [out] COR_VERSION     *version  
);  
```  
  
#### <a name="parameters"></a>參數  
 `version`  
 [out]儲存的執行階段的版本號碼 COR_VERSION 結構的指標。  
  
## <a name="remarks"></a>備註  
 `GetVersion`如果沒有執行階段載入處理序中，方法會傳回錯誤碼。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
