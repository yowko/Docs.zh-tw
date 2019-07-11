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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1054c7c977a487bb5a4bbf464322a65bcc039608
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755729"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue 方法
取得 ICorDebugValue 物件，其中包含指定的欄位所參考的靜態欄位值的介面指標權杖中指定的堆疊框架。  
  
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
 [in]`mdFieldDef`指定靜態欄位的語彙基元。  
  
 `pFrame`  
 [in]ICorDebugFrame 代表堆疊框架指標。  
  
 `ppValue`  
 [out]位址指標`ICorDebugValue`，其中包含靜態欄位的值。  
  
## <a name="remarks"></a>備註  
 `GetStaticFieldValue`方法可能只使用型別是 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，如所示[icordebugtype:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)方法。  
  
 對於非泛型型別，作業則是由執行`GetStaticFieldValue`等同於呼叫[icordebugclass:: Getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) ICorDebugClass 物件所傳回[icordebugtype:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).  
  
 泛型型別，對於靜態欄位值會相對於特定的具現化。 此外，如果相對於執行緒、 內容或應用程式定義域可能是靜態欄位，然後堆疊框架會協助偵錯工具判斷適當的值。  
  
## <a name="remarks"></a>備註  
 `GetStaticFieldValue` 可用時，才呼叫`ICorDebugType::GetType`傳回 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE 的值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
