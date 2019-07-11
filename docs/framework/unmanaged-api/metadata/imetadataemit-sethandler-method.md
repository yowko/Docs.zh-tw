---
title: IMetaDataEmit::SetHandler 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d50198cc6156d5bec8b8302a4624b0b7411a9c2d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751099"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler 方法
設定所指定參考的方法`IUnknown`指標當做權杖的重新對應的通知回呼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>參數  
 `pUnk`  
 [in]若要註冊處理常式。  
  
## <a name="remarks"></a>備註  
 中繼資料引擎會使用所提供的方法來傳送通知`SetHandler`，到編譯器，並不會記錄產生最佳化的方式，而且，想要最佳化已儲存的記錄。  
  
 如果未透過來提供回呼方法，則`SetHandler`，將會執行任何最佳化上儲存除了其中數個匯入範圍已合併使用`IMapToken`合併每個領域。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
