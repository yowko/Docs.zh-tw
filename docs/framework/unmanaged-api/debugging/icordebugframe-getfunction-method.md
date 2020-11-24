---
title: ICorDebugFrame::GetFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
ms.openlocfilehash: 9f9a6238057f56459eb8dca2375da412c3cd569d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690313"
---
# <a name="icordebugframegetfunction-method"></a>ICorDebugFrame::GetFunction 方法

取得包含與這個堆疊框架相關聯之程式碼的函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppFunction`  
 擴展ICorDebugFunction 物件位址的指標，該物件代表包含與這個堆疊框架相關聯之程式碼的函式。  
  
## <a name="remarks"></a>備註  

 `GetFunction`如果框架未與任何特定的函式相關聯，方法可能會失敗。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
