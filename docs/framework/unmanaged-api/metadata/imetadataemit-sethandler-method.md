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
ms.openlocfilehash: 60c9266806ef6b5d7e2e1c3a219a4485bc22d7f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler 方法
設定所指定參考的方法`IUnknown`指標當做權杖的重新對應的通知回呼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pUnk`  
 [in]若要註冊處理常式。  
  
## <a name="remarks"></a>備註  
 中繼資料引擎會使用所提供的方法來傳送通知`SetHandler`，編譯器，並不會記錄產生以最佳化方式，並想要最佳化儲存的記錄。  
  
 如果未透過來提供回呼方法，則`SetHandler`，將會執行任何最佳化上儲存除了其中數個匯入範圍已經合併使用`IMapToken`合併的每個範圍。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
