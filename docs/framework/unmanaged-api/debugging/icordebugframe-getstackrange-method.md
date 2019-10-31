---
title: ICorDebugFrame::GetStackRange 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
ms.openlocfilehash: 828e4dc67cb93d0a35879e94b54c9fac6e5bda16
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124076"
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange 方法
取得這個堆疊框架的絕對位址範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>參數  
 `pStart`  
 脫銷`CORDB_ADDRESS` 的指標，指定此 `ICorDebugFrame` 物件所表示之堆疊框架的起始位址。  
  
 `pEnd`  
 脫銷`CORDB_ADDRESS` 的指標，指定這個 `ICorDebugFrame` 物件所表示之堆疊框架的結束位址。  
  
## <a name="remarks"></a>備註  
 堆疊的位址範圍適用于將從多個偵錯工具收集而來的交錯堆疊追蹤 piecing 在一起。 此數值範圍不會提供有關堆疊框架之內容的資訊。 只有在比較堆疊框架位置時才有意義。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
