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
ms.openlocfilehash: d2e54f0b16300673409eb2f5757338dfa3011e61
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212993"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a>ICorDebugProcess2::GetDesiredNGENCompilerFlags 方法
取得目前的編譯器旗標設定，common language runtime （CLR）用來選取要載入此進程的正確先行編譯（也就是原生）影像。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `pdwFlags`  
 脫銷[CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md)列舉值的位元組合指標，用來選取要載入的正確先行編譯映射。  
  
## <a name="remarks"></a>備註  
 請使用[ICorDebugProcess2：： SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md)方法來設定旗標，以供 CLR 用來選取要載入的正確預先編譯影像。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
