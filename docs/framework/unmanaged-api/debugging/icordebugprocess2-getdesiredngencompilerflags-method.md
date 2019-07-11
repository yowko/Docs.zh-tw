---
title: ICorDebugProcess2::GetDesiredNGENCompilerFlags 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ee186604529a3e77a0217c5688df5b62ff8b28c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736990"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a>ICorDebugProcess2::GetDesiredNGENCompilerFlags 方法
取得目前的編譯器，common language runtime (CLR) 用來選取正確的先行編譯的旗標設定 (也就是原生) 映像載入此程序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `pdwFlags`  
 [out]指標的位元組合[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉值，用來選取要載入正確的先行編譯映像。  
  
## <a name="remarks"></a>備註  
 使用  [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)方法來設定 CLR 將用來選取正確的先行編譯映像載入的旗標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
