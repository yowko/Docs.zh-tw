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
ms.openlocfilehash: 4fa227d18b8cb10936d93fda9bcaf413ce63ca3b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003930"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler 方法
將指定之指標所參考的方法設定為權杖重新對應的 `IUnknown` 通知回呼。  
  
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
 中繼資料引擎會使用所提供的方法，將通知傳送 `SetHandler` 給不會以優化方式產生記錄，而且想要將儲存的記錄優化的編譯器。  
  
 如果未透過提供回呼方法，則 `SetHandler` 不會在儲存時執行優化，除非已 `IMapToken` 針對每個範圍使用 merge 合併數個匯入範圍。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
