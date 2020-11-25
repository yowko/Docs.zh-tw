---
title: ICorDebugEval2::NewStringWithLength 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: e5bab32f6d18c87b030f484a47bc3f1d525d2338
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729625"
---
# <a name="icordebugeval2newstringwithlength-method"></a>ICorDebugEval2::NewStringWithLength 方法

使用指定的內容，建立指定長度的字串。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a>參數  

 `string`  
 在字串值的指標。  
  
 `uiLength`  
 在字串的長度。  
  
## <a name="remarks"></a>備註  

 如果字串的尾端 null 字元應該在 managed 字串中，則方法的呼叫端 `NewStringWithLength` 必須確定字串長度包含尾端的 null 字元。  
  
 字串一律會建立線上程目前執行所在的應用程式域中。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
