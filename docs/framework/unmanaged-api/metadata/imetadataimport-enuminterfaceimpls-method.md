---
title: IMetaDataImport::EnumInterfaceImpls 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f6e4be2e05c573ec93cc23c8dd6eccc834b8b848
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136496"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls 方法
列舉所指定實作的所有介面`TypeDef`。 
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [in、 out]列舉值的指標。  
  
 `td`  
 [in]代表介面實作的 methoddef 語彙基元是要列舉的 TypeDef 語彙基元。  
  
 `rImpls`  
 [out]陣列，用來儲存 methoddef 語彙基元。  
  
 `cMax`  
 [in] `rImpls` 陣列的大小上限。  
  
 `pcImpls`  
 [out]權杖中傳回的實際數目`rImpls`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls` 已成功傳回。|  
|`S_FALSE`|沒有列舉 MethodDef 語彙基元。 在此情況下，`pcImpls`設為零。|  

## <a name="remarks"></a>備註

此列舉會傳回的集合`mdInterfaceImpl`每個介面實作所指定的語彙基元`TypeDef`。 介面權杖會傳回指定之介面的順序 (透過`DefineTypeDef`或`SetTypeDefProps`)。 屬性傳回之`mdInterfaceImpl`您可以使用查詢語彙基元[GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)。
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
