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
ms.openlocfilehash: da532ee1b5909a68bedbb9e6f6c96333e88002a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109719"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging 方法
控制即時（JIT）編譯器是否保留此模組內之方法的偵錯工具資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>參數  
 `bTrackJITInfo`  
 在將此值設定為 `true`，讓 JIT 編譯程式能夠保留此模組中每個方法的 Microsoft 中繼語言（MSIL）版本與 JIT 編譯版本之間的對應資訊。  
  
 `bAllowJitOpts`  
 在將此值設定為 `true`，讓 JIT 編譯程式能夠使用特定的 JIT 特定優化來產生程式碼以進行偵錯工具。  
  
## <a name="remarks"></a>備註  
 當偵錯工具作用中時，所有載入的模組預設會啟用 JIT 偵錯程式。 以程式設計方式啟用或停用設定會覆寫全域設定。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
