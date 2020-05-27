---
title: IMetaDataEmit::DeleteFieldMarshal 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
ms.openlocfilehash: 6d0f9a8c5c3baf7594e098a3d5544bad55fdc917
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009284"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a>IMetaDataEmit::DeleteFieldMarshal 方法
為指定之標記所參考的物件，終結 PInvoke 封送處理中繼資料簽章。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a>參數  
 `tk`  
 在`mdFieldDef`或 `mdParamDef` token，表示要刪除封送處理中繼資料簽章的欄位或參數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
