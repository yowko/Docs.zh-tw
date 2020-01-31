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
ms.openlocfilehash: 4799c1d04e8172c604eeec50f2b841a6db063949
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790575"
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
 應用程式域的清單是以呼叫 `EnumAppDomains` 方法時存在的應用程式域快照集為基礎。 這個方法可以被呼叫一次以上，以建立新的最新清單。 此方法的後續呼叫將不會影響現有的清單。  
  
 如果進程已經終止，`EnumAppDomains` 將會失敗，並出現 CORDBG_E_PROCESS_TERMINATED 的 HRESULT 值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorPublishProcess 介面](icorpublishprocess-interface.md)
