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
ms.openlocfilehash: 8aeb6ed448539db2720fee0d42cfcc344fd3bbf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762771"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging 方法
控制在 just-in-time (JIT) 編譯器是否會保留在這個模組中方法的偵錯資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>參數  
 `bTrackJITInfo`  
 [in]將此值設定為`true`若要啟用 JIT 編譯器保留的 Microsoft intermediate language (MSIL) 版本和 JIT 編譯的版本在此模組中的每個方法之間的對應資訊。  
  
 `bAllowJitOpts`  
 [in]將此值設定為`true`若要啟用 JIT 編譯器產生偵錯特定 JIT 特定最佳化的程式碼。  
  
## <a name="remarks"></a>備註  
 啟用偵錯工具時載入的所有模組的預設會啟用 JIT 偵錯。 以程式設計方式啟用或停用這些設定會覆寫全域設定。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
