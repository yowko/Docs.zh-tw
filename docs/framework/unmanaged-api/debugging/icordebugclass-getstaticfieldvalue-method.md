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
ms.openlocfilehash: d4a254853256e1a1440f5588418b94e39eabcc9a
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894101"
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
 在參考要`Def`抓取之欄位的欄位 token。  
  
 `pFrame`  
 在ICorDebugFrame 物件的指標，代表要用來區分執行緒、內容或應用程式域靜態變數的框架。  
  
 如果靜態欄位是相對於執行緒、內容或應用程式域，則此框架會決定適當的值。  
  
 `ppValue`  
 脫銷ICorDebugValue 物件位址的指標，表示靜態欄位的值。  
  
## <a name="remarks"></a>備註  
 針對參數化型別，靜態欄位的值是相對於特定具現化。 因此，如果類別的函式接受類型<xref:System.Type>的參數，請呼叫[ICorDebugType：： GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) ，而不是。 `ICorDebugClass::GetStaticFieldValue`  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
