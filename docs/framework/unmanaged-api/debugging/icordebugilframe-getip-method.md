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
ms.openlocfilehash: 314d2a06c8e246a42b315690dc9fe4b507db285a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703167"
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
 擴展指令指標的值。  
  
 `pMappingResult`  
 擴展CorDebugMappingResult 列舉值的位元組合指標，描述如何取得指令指標的值。  
  
## <a name="remarks"></a>備註  

 指令指標的值為函式之 Microsoft 中繼語言 (MSIL) 程式碼的堆疊框架位移。 如果堆疊框架為使用中，則此位址是下一個要執行的指令。 如果堆疊框架不在使用中，此位址是在堆疊框架重新開機時要執行的下一個指令。  
  
 如果這個框架是即時 (JIT) 編譯的框架，指令指標的值將會由從實際的原生指令指標反向對應來決定，因此值可能只是近似。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
