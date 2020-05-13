---
title: ICorDebugFunction::GetILCode 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
ms.openlocfilehash: 8c7be2d48a30a9f649c6d86e4edbc10085195b68
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213617"
---
# <a name="icordebugfunctiongetilcode-method"></a>ICorDebugFunction::GetILCode 方法
取得 ICorDebugCode 實例，代表與這個 ICorDebugFunction 物件相關聯的 Microsoft 中繼語言（MSIL）程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppCode`  
 脫銷實例的指標 `ICorDebugCode` ，如果函式未編譯為 MSIL，則為 null。  
  
## <a name="remarks"></a>備註  
 如果在這個函式上允許 [編輯後繼續]，則 `GetILCode` 方法會取得對應于 common language runtime （CLR）中之程式碼編輯版本的 MSIL 程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
