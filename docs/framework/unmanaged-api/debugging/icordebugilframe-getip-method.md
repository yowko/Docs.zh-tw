---
title: "ICorDebugILFrame::GetIP 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.GetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79b18c6fe15e28b2cec07ef9dfaa06ee295ab42d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP 方法
取得指令指標的值以及說明如何取得指令指標的值的位元組合值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pnOffset`  
 [out]指令指標的值。  
  
 `pMappingResult`  
 [out]CorDebugMappingResult 列舉值，描述如何取得指令指標的值的位元組合指標。  
  
## <a name="remarks"></a>備註  
 指令指標的值是函式的 Microsoft intermediate language (MSIL) 程式碼中堆疊框架的位移。 是否在作用中堆疊框架，此地址是要執行的下一個指令。 如果堆疊框架不是作用中，此位址就是下一個堆疊框架就會重新啟動時要執行指令。  
  
 如果這是在 just-in-time (JIT) 編譯的框架，指令指標的值取決於從實際的原生指令指標使用，因此值可能只是近似反向對應。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
