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
ms.openlocfilehash: 0cfc734e3c2d250bba045a926f5b178b6cbc1ba4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728195"
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
 擴展的指標 `CORDB_ADDRESS` ，指定這個物件所表示之堆疊框架的起始位址 `ICorDebugFrame` 。  
  
 `pEnd`  
 擴展的指標 `CORDB_ADDRESS` ，指定這個物件所表示之堆疊框架的結束位址 `ICorDebugFrame` 。  
  
## <a name="remarks"></a>備註  

 堆疊的位址範圍適用于將從多個偵測引擎收集而來的交錯堆疊追蹤 piecing 在一起。 數值範圍不提供堆疊框架內容的相關資訊。 它只有在比較堆疊框架位置時才有意義。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
