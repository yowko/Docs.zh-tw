---
title: "ICorDebugStepper::StepOut 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepOut
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b3ceca69b6b4710a3f1b8e1e9bdb4baf574119c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut 方法
會導致此 ICorDebugStepper 單一步驟透過其包含的執行緒，以及目前的框架將控制權傳回給呼叫的框架時，必須完成。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>備註  
 A`StepOut`之後從目前的框架正常傳回至呼叫的框架，才會完成作業。  
  
 如果`StepOut`時，會呼叫 unmanaged 程式碼，在目前的框架傳回至呼叫它的 managed 程式碼時，將完成步驟。  
  
 在.NET Framework 2.0 版中，請勿使用`StepOut`具有 STOP_UNMANAGED 旗標集因為它將會失敗。 (使用[icordebugstepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)將逐步執行的旗標設定。)Interop 偵錯工具必須跳離函式原生程式碼本身。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
