---
title: ICorDebugFunction::GetNativeCode 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
ms.openlocfilehash: 98aee38415709974d84873df50c39263490f2f23
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213266"
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode 方法
取得此 ICorDebugFunction 實例所表示之函式的原生程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppCode`  
 脫銷ICorDebugCode 實例的指標，表示此函式的機器碼，如果此函式是不是一次性（JIT）編譯的 Microsoft 中繼語言（MSIL）程式碼，則為 null。  
  
## <a name="remarks"></a>備註  
 如果這個實例所表示的函 `ICorDebugFunction` 式已多次進行 JIT 編譯，則在泛型型別的情況下，會傳回 `GetNativeCode` 隨機機器碼物件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
