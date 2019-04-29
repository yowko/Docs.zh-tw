---
title: EnumerateCLRs 函式
ms.date: 03/30/2017
api_name:
- EnumerateCLRs
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7532218728aead72186b5156da87db6d3bc0a8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698209"
---
# <a name="enumerateclrs-function"></a>EnumerateCLRs 函式
提供在處理程序中列舉 CLRs 的機制。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a>參數  
 `debuggeePID`  
 [in] 將列舉從 CLRs 載入之程序的處理序識別碼。  
  
 `ppHandleArrayOut`  
 [out] 使用於繼續 CLR 啟動，包含事件控制代碼的陣列的指標。 不保證在陣列中的每個控點是有效的。 如果有效，控制代碼將做為相對應執行階段位於`ppStringArrayOut` 的相同索引中的繼續啟動事件。  
  
 `ppStringArrayOut`  
 [out] 處理序中載入 CLRs 的指定完整路徑的字串陣列的指標。  
  
 `pdwArrayLengthOut`  
 [out] DWORD 指標，其中包含大小相等的 `ppHandleArrayOut` 和 `pdwArrayLengthOut` 長度。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 已成功確定處理序中的 CLR 數目，並且已正確填入對應的控制代碼和路徑陣列。  
  
 E_INVALIDARG  
 可能是 `ppHandleArrayOut` 或 `ppStringArrayOut` 為 null，或 `pdwArrayLengthOut` 為 null。  
  
 E_OUTOFMEMORY  
 函式無法為控制代碼和路徑陣列配置足夠的記憶體。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 無法列舉載入的 CLRs。  
  
## <a name="remarks"></a>備註  
 所識別之目標處理序 `debuggeePID`，此函式會傳回路徑的陣列，`ppStringArrayOut`，至 CLRs 載入到處理序；事件控制代碼陣列 `ppHandleArrayOut`，其中可能包含在相同的索引為 CLR 的繼續啟動事件；以及陣列的大小，`pdwArrayLengthOut`，指定 CLRs 載入的數目。  
  
 在 Windows 作業系統上，`debuggeePID` 對應至 OS 處理序識別碼。  
  
 記憶體 `ppHandleArrayOut` 和 `ppStringArrayOut` 由此函式所配置。 若要釋放配置的記憶體，您必須呼叫[CloseCLREnumeration 函式](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)。  
  
 參數設定為 null 的兩個陣列都可以呼叫此函式，以傳回目標處理序中的 CLRs 計數。 從這個計數，呼叫端可以推斷將建立的緩衝區大小：`(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** dbgshim.h  
  
 **程式庫：** dbgshim.dll  
  
 **.NET framework 版本：** 3.5 SP1
