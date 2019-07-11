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
ms.openlocfilehash: 2a5461cc6a78347cdbe0d0b13f8111cb24c11006
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760054"
---
# <a name="icordebuginternalframegetframetype-method"></a>ICorDebugInternalFrame::GetFrameType 方法
取得這個內部框架的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a>參數  
 `pType`  
 [out]CorDebugInternalFrameType 列舉，指出所表示的內部框架的類型值的指標`ICorDebugInternalFrame`物件。  
  
## <a name="remarks"></a>備註  
 內部框架類型絕對不會 STUBFRAME_NONE。 偵錯工具應該依正常程序會忽略無法辨識內部的畫面格型別。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
