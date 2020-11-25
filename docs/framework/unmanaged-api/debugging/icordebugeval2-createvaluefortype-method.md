---
title: ICorDebugEval2::CreateValueForType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: 0b17bd729733665fbc4645aecd2e588b7eba14bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729690"
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType 方法

取得指定類型之新 ICorDebugValue 的指標，其初始值為零或 null。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  

 `pType`  
 在代表類型之 ICorDebugType 物件的指標。  
  
 `ppValue`  
 擴展代表值之物件的位址指標 `ICorDebugValue` 。  
  
## <a name="remarks"></a>備註  

 `CreateValueForType` 一般化 [ICorDebugEval：： CreateValue](icordebugeval-createvalue-method.md) ，可讓您指定任意物件類型，包括之類的結構化類型 `List<int>` 。 這種方法的唯一目的是產生可傳遞給函數評估的值。  
  
 型別必須是類別或實值型別。 您無法使用這個方法來建立陣列值或字串值。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
