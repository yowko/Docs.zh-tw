---
title: "ICorDebugStepper::Deactivate 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.Deactivate
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 056d60a56c37126163361166e16da5d7949e2dbc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperdeactivate-method"></a>ICorDebugStepper::Deactivate 方法
會導致此 ICorDebugStepper 取消它所收到的最後一個步驟命令。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a>備註  
 已取消最近收到的步驟命令之後發出新的逐步執行指令。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
