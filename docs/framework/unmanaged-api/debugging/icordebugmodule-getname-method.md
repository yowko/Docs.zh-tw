---
title: ICorDebugModule::GetName 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
ms.openlocfilehash: b27e7a2cdcbfc3a88a734230118d99c2dd5c700e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129529"
---
# <a name="icordebugmodulegetname-method"></a>ICorDebugModule::GetName 方法
取得模組的檔案名。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `cchname`  
 [in] `szName` 陣列的大小。  
  
 `pcchName`  
 在傳回之名稱長度的指標。  
  
 `szName`  
 脫銷儲存傳回名稱的陣列。  
  
## <a name="remarks"></a>備註  
 如果模組的檔案名與磁片上的名稱相符，則 `GetName` 方法會傳回 S_OK HRESULT。 如果已製作名稱，`GetName` 會傳回 S_FALSE HRESULT，例如動態或記憶體中模組。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱
