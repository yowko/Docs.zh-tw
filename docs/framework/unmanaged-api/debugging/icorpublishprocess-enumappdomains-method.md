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
ms.openlocfilehash: 2acf8fb507ab617e066a31c9c2657b1ef0d18e47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693277"
---
# <a name="icorpublishprocessenumappdomains-method"></a>ICorPublishProcess::EnumAppDomains 方法

取得此 [ICorPublishProcess](icorpublishprocess-interface.md)所參考之進程中的應用程式域的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppEnum`  
 擴展 [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) 實例位址的指標，可讓您在這個進程中，透過應用程式域的集合進行反復專案。  
  
## <a name="remarks"></a>備註  

 應用程式域的清單是以呼叫方法時存在的應用程式域的快照集為基礎 `EnumAppDomains` 。 您可以多次呼叫這個方法來建立新的最新清單。 後續呼叫這個方法不會影響現有的清單。  
  
 如果進程已結束， `EnumAppDomains` 將會失敗，並出現 CORDBG_E_PROCESS_TERMINATED 的 HRESULT 值。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl、CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorPublishProcess 介面](icorpublishprocess-interface.md)
