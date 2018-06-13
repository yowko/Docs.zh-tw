---
title: ICorDebugChain::EnumerateFrames 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d408f317b546fb7e8314e904e6f5ad9e6296ae6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403262"
---
# <a name="icordebugchainenumerateframes-method"></a>ICorDebugChain::EnumerateFrames 方法
取得列舉值，其中包含鏈結中的所有受管理的堆疊框架開頭為最新的框架。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppFrames`  
 [out]ICorDebugFrameEnum 堆疊框架的列舉值物件的位址指標。  
  
## <a name="remarks"></a>備註  
 鏈結代表執行緒的實際呼叫堆疊。  
  
 `EnumerateFrames`方法應該呼叫只會針對受管理的鏈結。 偵錯 API 不提供方法以取得包含 unmanaged 鏈結中的框架。 偵錯工具必須使用其他方法來取得這項資訊。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
