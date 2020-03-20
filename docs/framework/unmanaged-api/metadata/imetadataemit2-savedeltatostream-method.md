---
title: IMetaDataEmit2::SaveDeltaToStream 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
ms.openlocfilehash: 7e8376f3a029b0e3ec51a1e7587dd14b3e7530ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177418"
---
# <a name="imetadataemit2savedeltatostream-method"></a>IMetaDataEmit2::SaveDeltaToStream 方法
將更改從當前編輯和繼續會話保存到指定的流。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `pIStream`  
 [在]指向要保存到的可寫流的介面指標。  
  
 `dwSaveFlags`  
 [in] 保留。 這個值必須為零。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
