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
ms.openlocfilehash: ef7057ad19fd34750bd15d358e9c1ebb1289cd44
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338056"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls 方法
列舉指定之 `TypeDef`所實作為的所有介面。 
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [in、out]列舉值的指標。  
  
 `td`  
 在要列舉其 MethodDef token 代表介面執行的 TypeDef 標記。  
  
 `rImpls`  
 脫銷用來儲存 MethodDef 標記的陣列。  
  
 `cMax`  
 在`rImpls` 陣列的最大長度。  
  
 `pcImpls`  
 脫銷`rImpls`中傳回的實際權杖數目。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|已成功傳回 `EnumInterfaceImpls`。|  
|`S_FALSE`|沒有要列舉的 MethodDef 標記。 在此情況下，`pcImpls` 會設定為零。|  

## <a name="remarks"></a>備註

列舉會針對指定 `TypeDef`所實的每個介面，傳回 `mdInterfaceImpl` token 的集合。 介面 token 會依照指定介面的順序傳回（透過 `DefineTypeDef` 或 `SetTypeDefProps`）。 您可以使用[GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)來查詢傳回之 `mdInterfaceImpl` token 的屬性。
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
