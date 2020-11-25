---
title: ICorDebugValue::GetAddress 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: 47c0c4dfa78e85bcc83f0bb2a333955c8e8666fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728364"
---
# <a name="icordebugvaluegetaddress-method"></a>ICorDebugValue::GetAddress 方法

取得這個 "ICorDebugValue" 物件的位址，此物件正在進行正在進行調試的進程中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a>參數  

 `pAddress`  
 擴展 `CORDB_ADDRESS` 物件的指標，該物件會指定這個值物件的位址。  
  
## <a name="remarks"></a>備註  

 如果無法使用此值，則會傳回 0 (零) 。 如果值至少部分在暫存器中，或儲存在垃圾收集行程控制碼 () ，就可能發生這種情況 `GCHandle` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
