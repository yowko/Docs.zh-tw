---
title: ICorDebugClass::GetStaticFieldValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b67f5ec233679461f61715d7562b47c2a195fb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750847"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>ICorDebugClass::GetStaticFieldValue 方法
取得指定的靜態欄位的值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `fieldDef`  
 [in]欄位`Def`參考要擷取欄位的語彙基元。  
  
 `pFrame`  
 [in]ICorDebugFrame 物件，表示要用來區分執行緒、 內容或應用程式網域的靜態變數的框架指標。  
  
 如果靜態欄位相對於執行緒、 內容或應用程式定義域中，框架會決定適當的值。  
  
 `ppValue`  
 [out]ICorDebugValue 物件，表示的靜態欄位值的位址指標。  
  
## <a name="remarks"></a>備註  
 參數化類型的靜態欄位的值是相對於特定的具現化。 因此，如果類別建構函式不接受參數的型別<xref:System.Type>，呼叫[icordebugtype:: Getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)而不是`ICorDebugClass::GetStaticFieldValue`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
