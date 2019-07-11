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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e32ce10b708afa5741d83cbd05f14accb4b2014f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754676"
---
# <a name="icordebugfunctiongetilcode-method"></a>ICorDebugFunction::GetILCode 方法
取得 ICorDebugCode 執行個體，表示與這個 ICorDebugFunction 物件相關聯的 Microsoft intermediate language (MSIL) 程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppCode`  
 [out]指標`ICorDebugCode`執行個體，則為 null，如果函式不編譯為 MSIL。  
  
## <a name="remarks"></a>備註  
 如果已在此函式，允許編輯後繼續`GetILCode`方法會對應到此函式已編輯版本的 common language runtime (CLR) 中的程式碼的 MSIL 程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
