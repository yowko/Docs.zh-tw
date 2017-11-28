---
title: "ICorDebugType::GetStaticFieldValue 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetStaticFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 34a37ef9a28dd0e6325db9bee61146f14d4638a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue 方法
取得 ICorDebugValue 物件，其中包含所指定的欄位參考的靜態欄位值的介面指標的指定之堆疊框架中語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fieldDef`  
 [in]`mdFieldDef`指定的靜態欄位的語彙基元。  
  
 `pFrame`  
 [in]代表堆疊框架 ICorDebugFrame 指標。  
  
 `ppValue`  
 [out]位址指標`ICorDebugValue`，其中包含靜態欄位值。  
  
## <a name="remarks"></a>備註  
 `GetStaticFieldValue`方法可能僅使用的類型為 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，由[icordebugtype:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)方法。  
  
 非泛型類型的作業則是由執行`GetStaticFieldValue`等同於呼叫[icordebugclass:: Getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) ICorDebugClass 物件傳回的上[icordebugtype:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).  
  
 泛型型別，靜態欄位值都是相對於特定的具現化。 此外，如果相對於執行緒、 內容或應用程式定義域可能是靜態欄位，然後堆疊框架可協助偵錯工具判斷正確的值。  
  
## <a name="remarks"></a>備註  
 `GetStaticFieldValue`可用時，才呼叫`ICorDebugType::GetType`傳回值的 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
