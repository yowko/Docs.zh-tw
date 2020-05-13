---
title: ICorDebugType::GetStaticFieldValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
ms.openlocfilehash: 83ac91133b226e2ac263356941c3fc3288355e7e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379941"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue 方法
取得 ICorDebugValue 物件的介面指標，其中包含指定之堆疊框架中指定欄位標記所參考的靜態欄位值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `fieldDef`  
 在`mdFieldDef`指定靜態欄位的 token。  
  
 `pFrame`  
 在代表堆疊框架之 ICorDebugFrame 的指標。  
  
 `ppValue`  
 脫銷位址的指標 `ICorDebugValue` ，其中包含靜態欄位的值。  
  
## <a name="remarks"></a>備註  
 `GetStaticFieldValue`只有在類型是 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE （如[ICorDebugType：： GetType](icordebugtype-gettype-method.md)方法所表示）時，才能使用方法。  
  
 針對非泛型型別，所執行的作業 `GetStaticFieldValue` 等同于在[ICorDebugType：： GetClass](icordebugtype-getclass-method.md)傳回的 ICorDebugClass 物件上呼叫[ICorDebugClass：： GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) 。  
  
 若是泛型型別，靜態域值會相對於特定的具現化。 此外，如果靜態欄位可能相對於執行緒、內容或應用程式域，則堆疊框架會協助偵錯工具判斷適當的值。  
  
## <a name="remarks"></a>備註  
 `GetStaticFieldValue`只有在的呼叫傳回 `ICorDebugType::GetType` ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE 的值時，才能使用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
