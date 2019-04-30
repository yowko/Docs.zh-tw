---
title: CreateVersionStringFromModule 函式
ms.date: 03/30/2017
api_name:
- CreateVersionStringFromModule
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ed8b85475dc7327c1aac6f920aba627215e27c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965798"
---
# <a name="createversionstringfrommodule-function"></a>CreateVersionStringFromModule 函式
從目標處理序中的 Common Language Runtime (CLR) 路徑來建立版本字串。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
## <a name="parameters"></a>參數  
 `pidDebuggee`  
 [in] 已載入目標 CLR 之處理序的識別碼。  
  
 `szModuleName`  
 [in] 載入處理序中之目標 CLR 的完整或相對路徑。  
  
 `pBuffer`  
 [out] 用來儲存目標 CLR 之版本字串的傳回緩衝區。  
  
 `cchBuffer`  
 [in] `pBuffer` 的大小。  
  
 `pdwLength`  
 [out] `pBuffer` 傳回之版本字串的長度。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 目標 CLR 的版本字串已成功傳回 `pBuffer` 中。  
  
 E_INVALIDARG  
 `szModuleName` 為 null，或者 `pBuffer` 或 `cchBuffer` 為 null。 `pBuffer` 和 `cchBuffer` 必須都是 null 或非 null。  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength` 大於 `cchBuffer`。 如果您為 `pBuffer` 和 `cchBuffer` 傳遞 null，並使用 `pdwLength` 來查詢所需的緩衝區大小，這可能是預期的結果。  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName` 未包含目標處理序中有效 CLR 的路徑。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 `pidDebuggee` 未參考有效的處理序，或其他失敗。  
  
## <a name="remarks"></a>備註  
 此函式可接受 `pidDebuggee` 識別的 CLR 處理序，以及 `szModuleName` 所指定的字串路徑。 版本字串傳回在 `pBuffer` 所指向的緩衝區中。 此字串對函式使用者是不透明的，也就是說，版本字串本身沒有內建意義。 它只會用在此函式的內容及[CreateDebuggingInterfaceFromVersion 函式](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)。  
  
 應該要呼叫此函式兩次。 當您第一次呼叫此函式時，針對 `pBuffer` 和 `cchBuffer` 都傳遞 null。 當您這麼做時，`pBuffer` 所需的緩衝區大小將會傳回 `pdwLength` 中。 然後您可以呼叫此函式第二次，並且在 `pBuffer` 中傳遞緩衝區，在 `cchBuffer` 中傳遞其大小。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** dbgshim.h  
  
 **程式庫：** dbgshim.dll  
  
 **.NET framework 版本：** 3.5 SP1
