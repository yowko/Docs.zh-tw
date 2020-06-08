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
ms.openlocfilehash: cac5aaa7ed13b6a48b36ad550da8b73d0deb2ee7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491039"
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
 在的大小（以寬字元為單位） `szProperty` 。  
  
 `pchProperty`  
 脫銷在中傳回的寬字元數 `szProperty` 。  
  
 `pdwPropFlags`  
 脫銷套用至屬性之任何屬性旗標的指標。 這個值是[CorPropertyAttr](corpropertyattr-enumeration.md)列舉中的位元遮罩。  
  
 `ppvSig`  
 脫銷屬性之中繼資料簽章的指標。  
  
 `pbSig`  
 脫銷在中傳回的位元組數目 `ppvSig` 。  
  
 `pdwCPlusTypeFlag`  
 脫銷指定常數類型的旗標，其為屬性的預設值。 此值來自 CorElementType 列舉。  
  
 `ppDefaultValue`  
 脫銷儲存這個屬性之預設值的位元組指標。  
  
 `pcchDefaultValue`  
 脫銷如果 ELEMENT_TYPE_STRING，則為的寬字元大小 `ppDefaultValue` `pdwCPlusTypeFlag` ; 否則，這個值就是不相關的。 在此情況下，的長度 `ppDefaultValue` 會從所指定的類型推斷 `pdwCPlusTypeFlag` 。  
  
 `pmdSetter`  
 脫銷MethodDef token 的指標，表示屬性的 set 存取子方法。  
  
 `pmdGetter`  
 脫銷MethodDef token 的指標，表示屬性的 get 存取子方法。  
  
 `rmdOtherMethod`  
 脫銷MethodDef 標記的陣列，表示與屬性相關聯的其他方法。  
  
 `cMax`  
 [in] `rmdOtherMethod` 陣列的大小上限。 如果您未提供足夠大的陣列來保存所有方法，則會略過，而不發出警告。  
  
 `pcOtherMethod`  
 脫銷在中傳回的 MethodDef 標記數目 `rmdOtherMethod` 。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
