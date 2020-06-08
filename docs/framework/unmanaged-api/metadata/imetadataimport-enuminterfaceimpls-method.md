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
ms.openlocfilehash: 910c40413075131765a37e00703ac892e3f39641
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492183"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls 方法
列舉由指定的所實作為的所有介面 `TypeDef` 。
  
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
 在陣列的最大長度 `rImpls` 。  
  
 `pcImpls`  
 脫銷在中傳回的實際權杖數目 `rImpls` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls`已成功傳回。|  
|`S_FALSE`|沒有要列舉的 MethodDef 標記。 在此情況下， `pcImpls` 會設定為零。|  

## <a name="remarks"></a>備註

列舉會 `mdInterfaceImpl` 針對所指定的每個介面傳回標記的集合 `TypeDef` 。 介面權杖會依照指定介面的順序（透過 `DefineTypeDef` 或 `SetTypeDefProps` ）傳回。 您 `mdInterfaceImpl` 可以使用[GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)來查詢傳回之權杖的屬性。
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
