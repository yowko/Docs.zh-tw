---
title: CloseCLREnumeration 函式
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9eb9bb1e4abeb98d8d0ba2b052612d918c45f22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741080"
---
# <a name="closeclrenumeration-function"></a>CloseCLREnumeration 函式
關閉任何有效 common language runtime (CLR) 繼續-啟動事件所傳回的控制代碼陣列中[EnumerateCLRs 函式](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)，並釋放用於控制代碼和字串路徑陣列的記憶體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a>參數  
 `pHandleArray`  
 [in]從傳回的事件控制代碼陣列的指標[EnumerateCLRs 函式](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)。  
  
 `pStringArray`  
 [in]從傳回的 CLR 字串路徑陣列的指標[EnumerateCLRs 函式](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)。  
  
 `dwArrayLength`  
 [in] 包含 `pHandleArray` 或 `pStringArray` 之大小 (長度) (兩者相同) 的 DWORD。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 開啟控制代碼[EnumerateCLRs 函式](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)已關閉，並釋放用於控制代碼和字串陣列配置記憶體。  
  
 E_INVALIDARG  
 `pHandleArray` 的長度不符合以 `dwArrayLength` 傳遞的長度。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 這個函式無法釋放用於 `pHandleArray` 和 `pStringArray` 的記憶體。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** dbgshim.h  
  
 **程式庫：** dbgshim.dll  
  
 **.NET framework 版本：** 3.5 SP1
