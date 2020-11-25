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
ms.openlocfilehash: a45f613b7547e2e80abdbd8ac85cb0b2b6a499e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716885"
---
# <a name="icorpublishgetprocess-method"></a>ICorPublish::GetProcess 方法

取得 [ICorPublishProcess](icorpublishprocess-interface.md) 實例，表示具有指定之識別碼的進程。  
  
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
 擴展表示進程之實例的位址指標 `ICorPublishProcess` 。  
  
## <a name="remarks"></a>備註  

 `GetProcess` 如果進程不存在，或不是可由目前使用者進行偵錯工具的 managed 進程，就會失敗。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl、CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorPublish 介面](icorpublish-interface.md)
