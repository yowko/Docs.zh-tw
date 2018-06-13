---
title: ICorDebugChain::GetThread 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 291c8129a790c235ee6e7f163c49c4e1e726cce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402708"
---
# <a name="icordebugchaingetthread-method"></a>ICorDebugChain::GetThread 方法
取得實體的執行緒，這個呼叫鏈結的一部分。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppThread`  
 [out]ICorDebugThread 物件，表示在實體執行緒的指標此呼叫鏈結是的一部分。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
