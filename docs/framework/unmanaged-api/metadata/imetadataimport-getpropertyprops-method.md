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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a08bd5beeb9fab1cd5b703c3afc4e82aaf71dbbc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122599"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps 方法
取得指定語彙基元所表示之屬性的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]語彙基元，表示要傳回的中繼資料的屬性。  
  
 `pClass`  
 [out]表示實作屬性的類型的 TypeDef 語彙基元指標。  
  
 `szProperty`  
 [out]若要保留的屬性名稱的緩衝區。  
  
 `cchProperty`  
 [in]寬字元大小`szProperty`。  
  
 `pchProperty`  
 [out]中傳回的寬字元數目`szProperty`。  
  
 `pdwPropFlags`  
 [out]任何套用至屬性的屬性旗標指標。 這個值是從位元遮罩[CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)列舉型別。  
  
 `ppvSig`  
 [out]中繼資料簽章屬性的指標。  
  
 `pbSig`  
 [out]中傳回的位元組數目`ppvSig`。  
  
 `pdwCPlusTypeFlag`  
 [out]旗標，指定類型的常數，它是屬性的預設值。 這個值是從 CorElementType 列舉型別。  
  
 `ppDefaultValue`  
 [out]儲存這個屬性的預設值的位元組指標。  
  
 `pcchDefaultValue`  
 [out]中的寬字元的大小`ppDefaultValue`，如果`pdwCPlusTypeFlag`是 ELEMENT_TYPE_STRING; 否則此值不相關。 在此情況下，長度`ppDefaultValue`會從所指定的型別推斷`pdwCPlusTypeFlag`。  
  
 `pmdSetter`  
 [out]表示屬性的 set 存取子方法的 MethodDef 語彙基元指標。  
  
 `pmdGetter`  
 [out]表示屬性的 get 存取子方法的 MethodDef 語彙基元指標。  
  
 `rmdOtherMethod`  
 [out]代表屬性相關聯的其他方法的 methoddef 語彙基元的陣列。  
  
 `cMax`  
 [in] `rmdOtherMethod` 陣列的大小上限。 如果您未提供足以容納所有方法的陣列，則會略過而不發出警告。  
  
 `pcOtherMethod`  
 [out]中傳回的 methoddef 語彙基元數目`rmdOtherMethod`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
