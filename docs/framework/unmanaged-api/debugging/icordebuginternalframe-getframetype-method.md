---
title: ICorDebugInternalFrame::GetFrameType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f7e5fceacc3fefa9267a9d7f989e745c392322e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebuginternalframegetframetype-method"></a>ICorDebugInternalFrame::GetFrameType 方法
取得這個內部框架的類型。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pType`  
 [out]CorDebugInternalFrameType 列舉，指出所表示的內部框架的類型值的指標`ICorDebugInternalFrame`物件。  
  
## <a name="remarks"></a>備註  
 內部框架類型絕對不會 STUBFRAME_NONE。 偵錯工具應該依正常程序會忽略無法辨識內部框架的類型。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
