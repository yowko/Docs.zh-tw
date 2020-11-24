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
ms.openlocfilehash: 223f66639ae24f2a54f1bc936f4a0765573356eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673887"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a>ICorDebugProcess2::GetDesiredNGENCompilerFlags 方法

取得 common language runtime (CLR) 用來選取正確先行編譯 (的目前編譯器旗標設定，也就是要載入此進程中的原生) 映射。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a>參數  

 `pdwFlags`  
 擴展 [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列舉值的位元組合指標，用來選取要載入的正確先行編譯映射。  
  
## <a name="remarks"></a>備註  

 您可以使用 [ICorDebugProcess2：： SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) 方法，設定 CLR 將用來選取要載入之正確預先編譯映射的旗標。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
