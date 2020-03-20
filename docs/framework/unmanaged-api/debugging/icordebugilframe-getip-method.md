---
title: ICorDebugILFrame::GetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: f30516a8f59b90de9b4c052d92a8c88575ace3c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178829"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP 方法
獲取指令指標的值和描述指令指標值的位組合值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>參數  
 `pnOffset`  
 [出]指令指標的值。  
  
 `pMappingResult`  
 [出]指向 CorDebugMappingResult 枚舉值的位狀組合的指標，用於描述如何獲取指令指標的值。  
  
## <a name="remarks"></a>備註  
 指令指標的值是堆疊幀的偏移量到函數的 Microsoft 中間語言 （MSIL） 代碼中。 如果堆疊幀處於活動狀態，則此位址是執行的下一個指令。 如果堆疊幀未處於活動狀態，則此位址是重新啟動堆疊幀時執行的下一個指令。  
  
 如果此幀是即時 （JIT） 編譯幀，則指令指標的值將通過從實際本機指令指標向後映射來確定，因此該值可能僅是近似值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
