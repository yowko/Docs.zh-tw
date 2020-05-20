---
title: ICorPublishProcess::EnumAppDomains 方法
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
ms.openlocfilehash: 0c3b5da52b78150198fa9f910bf01b4657e4eba8
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421159"
---
# <a name="icorpublishprocessenumappdomains-method"></a>ICorPublishProcess::EnumAppDomains 方法
取得此[ICorPublishProcess](icorpublishprocess-interface.md)所參考之進程中應用程式域的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppEnum`  
 脫銷[ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)實例位址的指標，允許在此進程中逐一查看應用程式域的集合。  
  
## <a name="remarks"></a>備註  
 應用程式域的清單是以呼叫方法時存在的應用程式域快照為基礎 `EnumAppDomains` 。 這個方法可以被呼叫一次以上，以建立新的最新清單。 此方法的後續呼叫將不會影響現有的清單。  
  
 如果進程已終止， `EnumAppDomains` 將會失敗，並產生 HRESULT 值 CORDBG_E_PROCESS_TERMINATED。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorPublishProcess 介面](icorpublishprocess-interface.md)
