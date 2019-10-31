---
title: ICorDebugFrame::CreateStepper 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
ms.openlocfilehash: 6ea2b24d37f56a5cb9e6b3dea0d666c8acc719dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091037"
---
# <a name="icordebugframecreatestepper-method"></a>ICorDebugFrame::CreateStepper 方法
取得分檔器，讓偵錯工具能夠執行相對於此 ICorDebugFrame 的逐步操作。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppStepper`  
 脫銷ICorDebugStepper 物件位址的指標，可讓偵錯工具執行相對於目前框架的逐步操作。  
  
## <a name="remarks"></a>備註  
 如果框架不在使用中，則在步驟完成之前，分檔器物件通常必須回到框架。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
