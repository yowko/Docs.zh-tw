---
title: ICorDebugEval::NewString 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
ms.openlocfilehash: c2d29a0cc344539bf515793c071fe839aa441ebc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729716"
---
# <a name="icordebugevalnewstring-method"></a>ICorDebugEval::NewString 方法

使用指定的內容配置新的字串實例。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a>參數  

 `string`  
 在字串內容的指標。  
  
## <a name="remarks"></a>備註  

 字串一律會建立線上程目前執行所在的應用程式域中。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
