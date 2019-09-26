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
ms.openlocfilehash: 3a05a779d4a56eb8f881da1824d5ffaa363b5a01
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274286"
---
# <a name="closeclrenumeration-function"></a>CloseCLREnumeration 函式
關閉位於[EnumerateCLRs](enumerateclrs-function.md)函式所傳回之控制碼陣列中的任何有效 common language RUNTIME （CLR）繼續-啟動事件，並釋放控制碼和字串路徑陣列的記憶體。  
  
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
 在從[EnumerateCLRs 函數](enumerateclrs-function.md)傳回之事件控制碼陣列的指標。  
  
 `pStringArray`  
 在從[EnumerateCLRs 函數](enumerateclrs-function.md)傳回之 CLR 字串路徑陣列的指標。  
  
 `dwArrayLength`  
 [in] 包含 `pHandleArray` 或 `pStringArray` 之大小 (長度) (兩者相同) 的 DWORD。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 [EnumerateCLRs](enumerateclrs-function.md)函式所開啟的控制碼已關閉，而且配置給控制碼和字串陣列的記憶體會被釋放。  
  
 E_INVALIDARG  
 `pHandleArray` 的長度不符合以 `dwArrayLength` 傳遞的長度。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 這個函式無法釋放用於 `pHandleArray` 和 `pStringArray` 的記憶體。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** dbgshim。h  
  
 連結**庫：** dbgshim  
  
 **.NET Framework 版本：** 3.5 SP1
