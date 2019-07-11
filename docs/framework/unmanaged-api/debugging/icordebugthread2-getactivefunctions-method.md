---
title: ICorDebugThread2::GetActiveFunctions 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdf3998d7430348cb71af8e7dd75cf2203d380ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769028"
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions 方法
在每個此執行緒的畫面格取得作用中的函式的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `cFunctions`  
 [in] `pFunctions` 陣列的大小。  
  
 `pcFunctions`  
 [out]中傳回的物件數目的指標`pFunctions`陣列。 傳回的物件數目會等於受控框架在堆疊上的數字。  
  
 `pFunctions`  
 [in、 out]COR_ACTIVE_FUNCTION 物件陣列，其中每個包含此執行緒的框架中作用中的函式的相關資訊。  
  
 第一個項目將用於分葉的框架，而且最後回到堆疊的根。  
  
## <a name="remarks"></a>備註  
 如果`pFunctions`為 null 輸入時，`GetActiveFunctions`傳回在堆疊上的函式的數目。 也就是說，如果`pFunctions`為 null 輸入時，`GetActiveFunctions`傳回值只能在`pcFunctions`。  
  
 `GetActiveFunctions`方法是做為最佳化透過從框架的堆疊追蹤，取得相同的資訊，因此包含原本 ICorDebugILFrame 物件為其完整的堆疊追蹤中的框架。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
