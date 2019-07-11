---
title: ICorDebugRegisterSet::SetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: debb704900d852df1d66c7bac65ab385e0d72ec5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769938"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a>ICorDebugRegisterSet::SetThreadContext 方法
`SetThreadContext` 未實作在.NET Framework 2.0 版。 請勿呼叫這個方法。  
  
> [!NOTE]
>  使用較高層級的作業[icordebugnativeframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)來設定執行緒的內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** 1.1, 1.0  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugRegisterSet 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
