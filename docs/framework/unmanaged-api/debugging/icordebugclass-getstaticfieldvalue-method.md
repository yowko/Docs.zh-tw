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
ms.openlocfilehash: dd1608badf553650b05b7de98d9bbcd76b2f3edf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728429"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>ICorDebugClass::GetStaticFieldValue 方法

取得指定之靜態欄位的值。  
  
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
 在 `Def` 參考要取出之欄位的欄位標記。  
  
 `pFrame`  
 在ICorDebugFrame 物件的指標，表示用來區分執行緒、內容或應用程式域靜態的框架。  
  
 如果靜態欄位相對於執行緒、內容或應用程式域，框架將會決定適當的值。  
  
 `ppValue`  
 擴展ICorDebugValue 物件位址的指標，該物件表示靜態欄位的值。  
  
## <a name="remarks"></a>備註  

 若為參數化型別，靜態欄位的值會相對於特定具現化。 因此，如果類別的函式採用型別的參數 <xref:System.Type> ，請呼叫 [ICorDebugType：： GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) 而不是 `ICorDebugClass::GetStaticFieldValue` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
