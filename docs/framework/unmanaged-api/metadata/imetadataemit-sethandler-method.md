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
ms.openlocfilehash: 9b03dc5460875af3bb3e5e20799a4d26eb74da05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730366"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler 方法

將指定指標所參考的方法設定 `IUnknown` 為 token 重新對應的通知回呼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>參數  

 `pUnk`  
 在要註冊的處理常式。  
  
## <a name="remarks"></a>備註  

 中繼資料引擎會使用所提供的方法，將通知傳送 `SetHandler` 至不以優化方式產生記錄，並想要將儲存的記錄優化的編譯器。  
  
 如果未透過提供回呼方法，則 `SetHandler` 不會在儲存時執行優化，但會在每個範圍的 merge 合併數個匯入範圍的情況下執行 `IMapToken` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
