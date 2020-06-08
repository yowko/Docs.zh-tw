---
title: IMetaDataEmit2::GetDeltaSaveSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: 24fe8fd65b36e133b767cd07c8602aa1ea7b9dfc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493093"
---
# <a name="imetadataemit2getdeltasavesize-method"></a>IMetaDataEmit2::GetDeltaSaveSize 方法
取得值，指出目前的「編輯後繼續」會話所產生之中繼資料大小的任何變更。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>參數  
 `fSave`  
 在其中一個[CorSaveSize](corsavesize-enumeration.md)值，表示所需的精確度層級。 針對 .NET Framework 版本2.0，會忽略這個參數。  
  
 `pdwSaveSize`  
 脫銷中繼資料大小的變更。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
- [IMetaDataEmit 介面](imetadataemit-interface.md)
