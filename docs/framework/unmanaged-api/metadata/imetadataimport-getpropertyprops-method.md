---
title: IMetaDataImport::GetPropertyProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 247a2793bf3806f5ee38585d50b4535820dfcb69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437067"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps 方法
取得指定標記所表示之屬性的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
## <a name="parameters"></a>參數  
 `prop`  
 在Token，表示要傳回中繼資料的屬性。  
  
 `pClass`  
 脫銷TypeDef token 的指標，代表實作為屬性的型別。  
  
 `szProperty`  
 脫銷保存屬性名稱的緩衝區。  
  
 `cchProperty`  
 在`szProperty`的寬字元大小。  
  
 `pchProperty`  
 脫銷`szProperty`中傳回的寬字元數。  
  
 `pdwPropFlags`  
 脫銷套用至屬性之任何屬性旗標的指標。 這個值是[CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)列舉中的位元遮罩。  
  
 `ppvSig`  
 脫銷屬性之中繼資料簽章的指標。  
  
 `pbSig`  
 脫銷`ppvSig`中傳回的位元組數目。  
  
 `pdwCPlusTypeFlag`  
 脫銷指定常數類型的旗標，其為屬性的預設值。 此值來自 CorElementType 列舉。  
  
 `ppDefaultValue`  
 脫銷儲存這個屬性之預設值的位元組指標。  
  
 `pcchDefaultValue`  
 脫銷`ppDefaultValue`的寬字元大小（如果 `pdwCPlusTypeFlag` ELEMENT_TYPE_STRING）;否則，這個值就是不相關的。 在這種情況下，`ppDefaultValue` 的長度是從 `pdwCPlusTypeFlag`所指定的類型推斷而來。  
  
 `pmdSetter`  
 脫銷MethodDef token 的指標，表示屬性的 set 存取子方法。  
  
 `pmdGetter`  
 脫銷MethodDef token 的指標，表示屬性的 get 存取子方法。  
  
 `rmdOtherMethod`  
 脫銷MethodDef 標記的陣列，表示與屬性相關聯的其他方法。  
  
 `cMax`  
 [in] `rmdOtherMethod` 陣列的大小上限。 如果您未提供足夠大的陣列來保存所有方法，則會略過，而不發出警告。  
  
 `pcOtherMethod`  
 脫銷`rmdOtherMethod`中傳回的 MethodDef 權杖數目。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
