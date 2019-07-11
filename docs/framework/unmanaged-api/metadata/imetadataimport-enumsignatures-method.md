---
title: IMetaDataImport::EnumSignatures 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58fa2a6d34f1f3627378c1355a1a292b665899ee
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756406"
---
# <a name="imetadataimportenumsignatures-method"></a>IMetaDataImport::EnumSignatures 方法
列舉代表目前範圍中獨立簽章的簽章語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [in、 out]列舉值的指標。 首次呼叫這個方法，這必須是 NULL。  
  
 `rSignatures`  
 [out]陣列，用來儲存簽章權杖。  
  
 `cMax`  
 [in] `rSignatures` 陣列的大小上限。  
  
 `pcSignatures`  
 [out]簽章權杖中傳回的數目`rSignatures`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumSignatures` 已成功傳回。|  
|`S_FALSE`|沒有列舉語彙基元。 在此情況下，`pcSignatures`為零。|  
  
## <a name="remarks"></a>備註  
 簽章權杖由[imetadataemit:: Gettokenfromsig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
