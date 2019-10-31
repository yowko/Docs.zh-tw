---
title: ICorDebugAssembly::GetName 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
ms.openlocfilehash: 5e3619d12b9377a8482254703d3d97d0348a013b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127163"
---
# <a name="icordebugassemblygetname-method"></a>ICorDebugAssembly::GetName 方法
取得此 `ICorDebugAssembly` 實例所代表之元件的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `cchName`  
 [in] `szName` 陣列的大小。  
  
 `pcchName`  
 脫銷整數的指標，指定名稱的實際長度。  
  
 `szName`  
 脫銷儲存名稱的陣列。  
  
## <a name="remarks"></a>備註  
 `GetName` 方法會傳回元件的完整路徑和檔案名。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
