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
ms.openlocfilehash: 7e1605eede55360e72d65da6744bc1dcce4f107f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130996"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP 方法
取得指令指標的值，以及描述如何取得指令指標值的位組合值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>參數  
 `pnOffset`  
 脫銷指令指標的值。  
  
 `pMappingResult`  
 脫銷CorDebugMappingResult 列舉值的位元組合指標，描述如何取得指令指標的值。  
  
## <a name="remarks"></a>備註  
 指令指標的值是函式的 Microsoft 中繼語言（MSIL）程式碼的堆疊框架位移。 如果堆疊框架作用中，此位址就是下一個要執行的指令。 如果堆疊框架不在使用中，此位址就是在堆疊框架重新開機時要執行的下一個指令。  
  
 如果此框架是即時（JIT）編譯的框架，則指令指標的值將由從實際的原生指令指標向後對應來決定，因此值可能只是近似值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
