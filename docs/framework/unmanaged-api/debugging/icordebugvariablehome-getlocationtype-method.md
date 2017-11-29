---
title: "ICorDebugVariableHome::GetLocationType 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetLocationType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a600f26440e29a60d776be8679d7a298d77434f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomegetlocationtype-method"></a>ICorDebugVariableHome::GetLocationType 方法
取得變數的原生位置類型。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pLocationType`  
 [out]變數的原生位置的類型的指標。  請參閱[VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)列舉型別，如需詳細資訊。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugVariableHome 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [VariableLocationType 列舉](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
