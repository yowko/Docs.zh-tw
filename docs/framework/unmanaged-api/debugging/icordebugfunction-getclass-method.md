---
title: ICorDebugFunction::GetClass 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 184e578efb549a1dc2e9ec1e30a29ff289b68719
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugfunctiongetclass-method"></a>ICorDebugFunction::GetClass 方法
取得 ICorDebugClass 物件，表示此函式所屬的類別。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppClass`  
 [out]位址指標`ICorDebugClass`表示物件的類別或為 null，如果此函式不是類別的成員。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
