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
ms.openlocfilehash: 5fc71bf240b89afadbf8f2ba10906322921bdda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175326"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps 方法
獲取指定權杖表示的屬性的中繼資料。  
  
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
 [在]表示要為其返回中繼資料的屬性的權杖。  
  
 `pClass`  
 [出]指向 TypeDef 權杖的指標，表示實現該屬性的類型。  
  
 `szProperty`  
 [出]保存屬性名稱的緩衝區。  
  
 `cchProperty`  
 [在]以 寬字元表示`szProperty`的大小。  
  
 `pchProperty`  
 [出]在 中`szProperty`返回的寬字元數。  
  
 `pdwPropFlags`  
 [出]指向應用於該屬性的任何屬性標誌的指標。 此值是[CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)枚舉中的位元遮罩。  
  
 `ppvSig`  
 [出]指向屬性的中繼資料簽名的指標。  
  
 `pbSig`  
 [出]在 中`ppvSig`返回的位元組數。  
  
 `pdwCPlusTypeFlag`  
 [出]指定作為屬性預設值的常量類型的標誌。 此值來自 CorElementType 枚舉。  
  
 `ppDefaultValue`  
 [出]指向存儲此屬性的預設值的位元組的指標。  
  
 `pcchDefaultValue`  
 [出]大字元的大小`ppDefaultValue`，如果`pdwCPlusTypeFlag`為ELEMENT_TYPE_STRING;否則，此值不相關。 在這種情況下，將從 指定的類型推斷`ppDefaultValue`的長度`pdwCPlusTypeFlag`。  
  
 `pmdSetter`  
 [出]指向 MethodDef 權杖的指標，表示屬性的設置訪問器方法。  
  
 `pmdGetter`  
 [出]指向 MethodDef 權杖的指標，表示屬性的 get 訪問器方法。  
  
 `rmdOtherMethod`  
 [出]表示與屬性關聯的其他方法的 MethodDef 權杖陣列。  
  
 `cMax`  
 [in] `rmdOtherMethod` 陣列的大小上限。 如果提供的陣列足夠大以容納所有方法，則不會發出警告即可跳過這些方法。  
  
 `pcOtherMethod`  
 [出]在 中`rmdOtherMethod`返回的 MethodDef 權杖數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
