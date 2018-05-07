---
title: ICorDebugModule::EnableJITDebugging 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71722293bfb80a7e57393916560f922d970ea2ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging 方法
控制是否在 just-in-time (JIT) 編譯器會保留在這個模組中方法的偵錯資訊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bTrackJITInfo`  
 [in]將此值設定為`true`以啟用 JIT 編譯器保留的 Microsoft intermediate language (MSIL) 版本與此模組中的每個方法的 JIT 編譯版本之間的對應資訊。  
  
 `bAllowJitOpts`  
 [in]將此值設定為`true`以啟用 JIT 編譯器產生的程式碼與偵錯特定特定的 JIT 最佳化。  
  
## <a name="remarks"></a>備註  
 偵錯工具為作用中時，會載入的所有模組的預設會啟用 JIT 偵錯。 以程式設計方式啟用或停用這些設定會覆寫全域設定。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
