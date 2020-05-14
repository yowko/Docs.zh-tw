---
title: ICoreClrDebugTarget::EnumRuntimes 方法
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
ms.openlocfilehash: fc8269d4cc22ab53569edaa48c27b4a01970dcc7
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397179"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>ICoreClrDebugTarget::EnumRuntimes 方法
列舉遠端電腦上所執行之指定處理序中的 Common Language Runtime (CLR)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a>參數  
 `dwInternalProcessID`  
 [in] 要列舉執行階段之處理序的內部處理序 ID。 這會 `m_dwInternalID` 來自對應的[CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md)。  
  
 `pcRuntimes`  
 [out] `ppRuntimes` 中傳回的執行階段數目。 這個值可以是 0 (零)。  
  
 `ppRuntimes`  
 脫銷[CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md)結構的陣列，代表在遠端目標進程中載入的執行時間。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 成功。  
  
 S_FALSE  
 `dwInternalProcessID` 不符合電腦上所執行的任何處理序，可能是因為處理序已終止。 `pcRuntimes` 和 `ppRuntimes` 將為 null。  
  
 E_OUTOFMEMORY  
 無法為 `ppRuntimes` 配置足夠的記憶體。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 其他失敗。  
  
## <a name="remarks"></a>備註  
 若要釋放這個方法所配置的記憶體，請呼叫[ICoreClrDebugTarget：： FreeMemory](icoreclrdebugtarget-freememory-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CoreClrRemoteDebuggingInterfaces。h  
  
 連結**庫：** mscordbi_macx86 .dll  
  
 **.NET Framework 版本：** 3.5 SP1  
  
## <a name="see-also"></a>請參閱

- [ICoreClrDebugTarget 介面](icoreclrdebugtarget-interface.md)
