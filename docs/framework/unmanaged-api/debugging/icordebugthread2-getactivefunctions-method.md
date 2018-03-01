---
title: "ICorDebugThread2::GetActiveFunctions 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ecd9446f642011b21f784019f583f49e3a70433a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions 方法
在每個執行緒框架中取得作用中的函式的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cFunctions`  
 [in] `pFunctions` 陣列的大小。  
  
 `pcFunctions`  
 [out]傳回的物件數目的指標`pFunctions`陣列。 傳回的物件數目會等於 managed 堆疊框架數目。  
  
 `pFunctions`  
 [in、 out]COR_ACTIVE_FUNCTION 物件陣列，其中每一個都包含在這個執行緒框架中作用中的函式的相關資訊。  
  
 第一個項目將用於分葉框架和堆疊的根目錄等等上一步。  
  
## <a name="remarks"></a>備註  
 如果`pFunctions`為輸入時，null`GetActiveFunctions`傳回在堆疊上的函式的數目。 也就是說，如果`pFunctions`為輸入時，null`GetActiveFunctions`傳回值，僅在`pcFunctions`。  
  
 `GetActiveFunctions`方法主要為了最佳化透過由框架的堆疊追蹤取得相同的資訊並包含原本 ICorDebugILFrame 物件為其完整的堆疊追蹤中的框架。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
