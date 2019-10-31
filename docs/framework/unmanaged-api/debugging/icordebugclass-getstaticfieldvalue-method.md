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
ms.openlocfilehash: 867db3325f9b18b31f66429d01ea02be3603c0f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125753"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>ICorDebugClass::GetStaticFieldValue 方法
取得指定靜態欄位的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `fieldDef`  
 在欄位 `Def` token，此權杖會參考要抓取的欄位。  
  
 `pFrame`  
 在ICorDebugFrame 物件的指標，代表要用來區分執行緒、內容或應用程式域靜態變數的框架。  
  
 如果靜態欄位是相對於執行緒、內容或應用程式域，則此框架會決定適當的值。  
  
 `ppValue`  
 脫銷ICorDebugValue 物件位址的指標，表示靜態欄位的值。  
  
## <a name="remarks"></a>備註  
 針對參數化型別，靜態欄位的值是相對於特定具現化。 因此，如果類別的函式接受 <xref:System.Type>類型的參數，請呼叫[ICorDebugType：： GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) ，而不是 `ICorDebugClass::GetStaticFieldValue`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
