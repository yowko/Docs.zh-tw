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
ms.openlocfilehash: 2d5674d6b5962ca539de02cda1e5658daed83622
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678746"
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions 方法

取得此執行緒的每個框架中作用中函式的相關資訊。  
  
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
 擴展陣列中傳回的物件數目指標 `pFunctions` 。 傳回的物件數目會等於堆疊上的 managed 框架數目。  
  
 `pFunctions`  
 [in，out]COR_ACTIVE_FUNCTION 物件的陣列，其中每個物件都包含此執行緒框架中作用中函式的相關資訊。  
  
 第一個元素會用於分葉框架，然後回到堆疊的根目錄。  
  
## <a name="remarks"></a>備註  

 如果 `pFunctions` 輸入上的是 null，則 `GetActiveFunctions` 只會傳回堆疊上的函式數目。 也就是說，如果 `pFunctions` 輸入上的是 null，則 `GetActiveFunctions` 只會在中傳回值 `pcFunctions` 。  
  
 `GetActiveFunctions`方法的目的是要從堆疊追蹤中的框架取得相同資訊的優化，而且只包含在完整堆疊追蹤中具有 ICorDebugILFrame 物件的框架。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
