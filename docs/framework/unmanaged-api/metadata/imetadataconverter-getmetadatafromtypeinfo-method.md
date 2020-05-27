---
title: IMetaDataConverter::GetMetaDataFromTypeInfo 方法
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeInfo
helpviewer_keywords:
- GetMetaDataFromTypeInfo method [.NET Framework metadata]
- IMetaDataConverter::GetMetaDataFromTypeInfo method [.NET Framework metadata]
ms.assetid: d44484bb-23a3-49c3-9e46-69d0d9ab4f0f
topic_type:
- apiref
ms.openlocfilehash: f9f3e3f196f74a7dea3c722925f1d03968688882
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008998"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a>IMetaDataConverter::GetMetaDataFromTypeInfo 方法
取得[IMetaDataImport](imetadataimport-interface.md)實例的指標，表示指定之實例所參考之類型程式庫的中繼資料簽章 `ITypeInfo` 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a>參數  
 `pITI`  
 在參考型別連結 `ITypeInfo` 庫之物件的指標。  
  
 `ppMDI`  
 脫銷位置的指標，接收代表中繼資料簽章之 `IMetaDataImport` 實例的位址。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
