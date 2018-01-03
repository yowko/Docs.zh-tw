---
title: "ICorDebugArrayValue::GetElementAtPosition 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.GetElementAtPosition
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c26a55815e57126895902275148940c5271c235b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a>ICorDebugArrayValue::GetElementAtPosition 方法
取得陣列視為的以零為起始的一維陣列的指定位置處的元素。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `nPosition`  
 [in]要擷取之項目的位置。  
  
 `ppValue`  
 [out]ICorDebugValue 物件，表示項目的值的位址指標。  
  
## <a name="remarks"></a>備註  
 多維度陣列的配置會遵循陣列配置的 c + + 樣式。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
