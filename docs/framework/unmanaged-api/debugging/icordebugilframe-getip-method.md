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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a7b8985e7580282d0e38205f9b1d6078f86cee6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988607"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP 方法
取得指令指標的值和描述如何取得指令指標的值的位元組合值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>參數  
 `pnOffset`  
 [out]指令指標的值。  
  
 `pMappingResult`  
 [out]CorDebugMappingResult 列舉值，描述如何取得指令指標的值的位元組合指標。  
  
## <a name="remarks"></a>備註  
 指令指標的值是函式的 Microsoft intermediate language (MSIL) 程式碼的堆疊框架的位移。 如果作用中堆疊框架，此位址會是下一個要執行的指令。 如果堆疊框架不是作用中，此位址會是堆疊框架就會重新啟動時要執行的下一個指令。  
  
 如果這是在 just-in-time (JIT) 編譯的框架，指令指標的值會取決從實際的原生指令指標使用，因此值可能只是近似反向對應。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
