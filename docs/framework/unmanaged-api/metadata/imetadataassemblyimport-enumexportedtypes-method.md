---
title: IMetaDataAssemblyImport::EnumExportedTypes 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: f00fe5bce2f808265add228406dfaa2ccc267545
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176002"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a>IMetaDataAssemblyImport::EnumExportedTypes 方法
枚舉當前中繼資料作用域中組件資訊清單中引用的匯出類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [進出]指向枚舉器的指標。 當首次調用該方法時，`EnumExportedTypes`這必須是 null 值。  
  
 `rExportedTypes`  
 [出]中繼資料權杖的`mdExportedType`枚舉。  
  
 `cMax`  
 [在]可放置在`rExportedTypes`陣列中`mdExportedType`的最大權杖數。  
  
 `pcTokens`  
 [出]實際放置在`mdExportedType`中的`rExportedTypes`權杖數。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumExportedTypes`已成功返回。|  
|`S_FALSE`|沒有要枚舉的權杖。 在這種情況下，`pcTokens`設置為零。|  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
