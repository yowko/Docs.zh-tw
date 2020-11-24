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
ms.openlocfilehash: 575e194cf952f02a3fe4fce9e955e45e1bc3653d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673909"
---
# <a name="closeclrenumeration-function"></a>CloseCLREnumeration 函式

關閉任何有效的 common language runtime (CLR) 繼續 [EnumerateCLRs](enumerateclrs-function.md)函式所傳回之控制碼陣列中的啟動事件，並釋放控制碼和字串路徑陣列的記憶體。  
  
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
 在從 [EnumerateCLRs](enumerateclrs-function.md)函式傳回之事件控制碼陣列的指標。  
  
 `pStringArray`  
 在從 [EnumerateCLRs](enumerateclrs-function.md)函式傳回之 CLR 字串路徑陣列的指標。  
  
 `dwArrayLength`  
 [in] 包含 `pHandleArray` 或 `pStringArray` 之大小 (長度) (兩者相同) 的 DWORD。  
  
## <a name="return-value"></a>傳回值  

 S_OK  
 [EnumerateCLRs](enumerateclrs-function.md)函式所開啟的控制碼已關閉，而配置給控制碼和字串陣列的記憶體則會釋放。  
  
 E_INVALIDARG  
 `pHandleArray` 的長度不符合以 `dwArrayLength` 傳遞的長度。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 這個函式無法釋放用於 `pHandleArray` 和 `pStringArray` 的記憶體。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** dbgshim。h  
  
 連結 **庫：** dbgshim.dll  
  
 **.NET Framework 版本：** 3.5 SP1
