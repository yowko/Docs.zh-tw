---
title: ICoreClrDebugTarget::EnumProcesses 方法
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
ms.openlocfilehash: 6484832e8e737b9a0d0b3eaf3ede4078729f7a4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178431"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>ICoreClrDebugTarget::EnumProcesses 方法
列舉在遠端電腦上執行的處理序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a>參數  
 `pcProcs`  
 [out] `ppProcs` 中傳回的處理序數目。 這個值可以是 0 (零)。  
  
 `ppProcs`  
 [出]一個[CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md)結構的陣列，表示在遠端電腦上運行的進程。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 成功。  
  
 E_OUTOFMEMORY  
 無法為 `ppProcs` 配置足夠的記憶體。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 其他失敗。  
  
## <a name="remarks"></a>備註  
 要釋放此方法分配的記憶體，請調用[ICoreClrDebugTarget：：freeMemory](icoreclrdebugtarget-freememory-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 核心Clr遠端偵錯介面.h  
  
 **資料庫：** mscordbi_macx86.dll  
  
 **.NET 框架版本：** 3.5 SP1  
  
## <a name="see-also"></a>另請參閱

- [ICoreClrDebugTarget 介面](icoreclrdebugtarget-interface.md)
