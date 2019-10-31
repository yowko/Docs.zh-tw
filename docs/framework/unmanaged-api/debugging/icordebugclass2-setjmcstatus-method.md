---
title: ICorDebugClass2::SetJMCStatus 方法
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
ms.openlocfilehash: a862dd3f6a9c10c6b3a5a0bb41208d351c4ca9f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125696"
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus 方法
針對類別的每個方法，設定一個值，指出此方法是否為使用者定義的程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>參數  
 `bIsJustMyCode`  
 在設定為 `true`，表示該方法是使用者定義的程式碼;否則，請將設定為 `false`。  
  
## <a name="remarks"></a>備註  
 只有 my code （JMC）分檔器會略過非使用者定義的程式碼。 使用者定義的程式碼必須是可偵錯工具代碼的子集。  
  
 如果不能設定任何方法的值，則 `SetJMCStatus` 會傳回值為 S_FALSE 的 HRESULT，即使它成功設定所有其他方法的值也一樣。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
