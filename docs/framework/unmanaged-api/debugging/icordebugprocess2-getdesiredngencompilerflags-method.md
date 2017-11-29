---
title: "ICorDebugProcess2::GetDesiredNGENCompilerFlags 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 46d366f27c7b7eec8018f2095388fef4e6204205
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a>ICorDebugProcess2::GetDesiredNGENCompilerFlags 方法
取得目前的編譯器，common language runtime (CLR) 用來選取正確的先行編譯的旗標設定 (也就是原生) 載入此處理序的映像。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwFlags`  
 [out]指標的位元組合[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉值，用來選取要載入正確的先行編譯映像。  
  
## <a name="remarks"></a>備註  
 使用[icordebugprocess2:: Setdesiredngencompilerflags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)方法，以設定 CLR 將用來選取正確的先行編譯映像載入的旗標。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
