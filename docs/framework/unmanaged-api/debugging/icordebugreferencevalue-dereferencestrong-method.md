---
title: ICorDebugReferenceValue::DereferenceStrong 方法
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.DereferenceStrong
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::DereferenceStrong
helpviewer_keywords:
- ICorDebugReferenceValue::DereferenceStrong method [.NET Framework debugging]
- DereferenceStrong method [.NET Framework debugging]
ms.assetid: 723482d1-d1a1-410a-a405-677eeb04e2bf
topic_type:
- apiref
ms.openlocfilehash: 402ffa232691bc8d0c77a9fa5aeb524dd5a9409b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137733"
---
# <a name="icordebugreferencevaluedereferencestrong-method"></a>ICorDebugReferenceValue::DereferenceStrong 方法
未執行 `DereferenceStrong`。 請勿呼叫此方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DereferenceStrong (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
