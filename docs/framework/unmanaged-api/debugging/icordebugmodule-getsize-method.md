---
title: ICorDebugModule::GetSize 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0d741bda5426dee1292df0e6fd9107cc2f44c8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodulegetsize-method"></a>ICorDebugModule::GetSize 方法
取得大小，以位元組為單位的模組。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcBytes`  
 [out]以位元組為單位之模組的大小。  
  
 如果從原生映像產生器 (NGen.exe) 產生的模組，模組的大小將是零。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
