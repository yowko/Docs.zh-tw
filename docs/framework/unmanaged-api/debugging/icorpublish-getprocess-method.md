---
title: ICorPublish::GetProcess 方法
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
ms.openlocfilehash: a9d28243e9907fcc6320b2e09a49312bf35a70b4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121780"
---
# <a name="icorpublishgetprocess-method"></a>ICorPublish::GetProcess 方法
取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)實例，表示具有指定之識別碼的進程。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a>參數  
 `pid`  
 在進程的識別碼。  
  
 `ppProcess`  
 脫銷代表進程之 `ICorPublishProcess` 實例位址的指標。  
  
## <a name="remarks"></a>備註  
 如果進程不存在，或不是目前使用者可以進行的 managed 進程，`GetProcess` 會失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorPublish 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
