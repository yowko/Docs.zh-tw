---
title: IMetaDataImport::EnumCustomAttributes 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 61b5678a546bdbadbcc6d8ee86447cb17ce72b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175521"
---
# <a name="imetadataimportenumcustomattributes-method"></a>IMetaDataImport::EnumCustomAttributes 方法
枚舉與指定類型或成員關聯的自訂屬性定義權杖。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [進出]指向返回的枚舉器的指標。  
  
 `tk`  
 [在]枚舉範圍的標記，所有自訂屬性為零。  
  
 `tkType`  
 [在]要枚舉的屬性類型的建構函式或`null`所有類型的建構函式的權杖。  
  
 `rCustomAttributes`  
 [出]自訂屬性權杖的陣列。  
  
 `cMax`  
 [in] `rCustomAttributes` 陣列的大小上限。  
  
 `pcCustomAttributes`  
 [退出，可選]在 中`rCustomAttributes`返回的權杖值的實際數量。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes`已成功返回。|  
|`S_FALSE`|沒有要枚舉的自訂屬性。 在這種情況下，`pcCustomAttributes`為零。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
