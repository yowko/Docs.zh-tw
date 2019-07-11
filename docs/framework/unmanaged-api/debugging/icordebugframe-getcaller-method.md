---
title: ICorDebugFrame::GetCaller 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a637cebb9e1aef20c600353eb14fe900ad7513c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754167"
---
# <a name="icordebugframegetcaller-method"></a>ICorDebugFrame::GetCaller 方法
取得在目前的鏈結中，呼叫此框架 ICorDebugFrame 物件指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppFrame`  
 [out]位址指標`ICorDebugFrame`物件，表示呼叫端的框架。 此值為 null 如果被呼叫的框架是目前的鏈結中最外層的框架。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
