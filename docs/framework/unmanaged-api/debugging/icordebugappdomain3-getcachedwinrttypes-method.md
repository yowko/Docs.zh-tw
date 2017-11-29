---
title: "ICorDebugAppDomain3::GetCachedWinRTTypes 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3.GetCachedWinRTTypes
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fb41b278b21b2289c7f5a7164a1bd01bc39423b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypes 方法
取得列舉值，所有快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
#### <a name="parameters"></a>參數  
 `ppGuidToTypeEnum`  
 [out]指標[ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)介面物件的可列舉的受管理的表示法[!INCLUDE[wrt](../../../../includes/wrt-md.md)]目前載入的應用程式定義域中的類型。  
  
## <a name="requirements"></a>需求  
 **平台：**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugAppDomain3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
