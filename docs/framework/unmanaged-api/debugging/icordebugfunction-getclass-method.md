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
ms.openlocfilehash: 40cb59a2ad0539764702369b13d632eddbab8174
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728156"
---
# <a name="icordebugfunctiongetclass-method"></a>ICorDebugFunction::GetClass 方法

取得 ICorDebugClass 物件，這個物件表示此函式所屬的類別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppClass`  
 擴展代表類別之物件位址的指標 `ICorDebugClass` ，如果此函式不是類別的成員，則為 null。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
