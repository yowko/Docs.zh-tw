---
title: ICorDebugEval::GetResult 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
ms.openlocfilehash: 86c017f581c7b980b8b0cb8bd7bdc1b0aa439afe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705815"
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult 方法

取得此評估的結果。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppResult`  
 擴展ICorDebugValue 物件位址的指標，該物件代表此評估的結果（如果評估正常完成）。  
  
## <a name="remarks"></a>備註  

 `GetResult`只有在評估完成後，此方法才有效。  
  
 如果評估正常完成，則會 `ppResult` 指定結果。 如果它以例外狀況結束，則結果為擲回的例外狀況。 如果評估是針對新的物件，則結果會是新物件的參考。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
