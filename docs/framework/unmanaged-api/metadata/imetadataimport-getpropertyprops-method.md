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
ms.openlocfilehash: aded23e190de18d76bb2b9e2ffbae51cf2325419
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729222"
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
 在表示傳回中繼資料之屬性的 token。  
  
 `pClass`  
 擴展TypeDef token 的指標，代表實作為屬性的型別。  
  
 `szProperty`  
 擴展保存屬性名稱的緩衝區。  
  
 `cchProperty`  
 在的大小（以寬字元為單位） `szProperty` 。  
  
 `pchProperty`  
 擴展傳回的寬字元數 `szProperty` 。  
  
 `pdwPropFlags`  
 擴展套用至屬性之任何屬性旗標的指標。 這個值是 [CorPropertyAttr](corpropertyattr-enumeration.md) 列舉的位元遮罩。  
  
 `ppvSig`  
 擴展屬性之中繼資料簽章的指標。  
  
 `pbSig`  
 擴展傳回的位元組數目 `ppvSig` 。  
  
 `pdwCPlusTypeFlag`  
 擴展旗標，指定屬於屬性預設值的常數型別。 此值來自 CorElementType 列舉。  
  
 `ppDefaultValue`  
 擴展儲存這個屬性之預設值的位元組指標。  
  
 `pcchDefaultValue`  
 擴展如果 ELEMENT_TYPE_STRING，則為寬字元的大小 `ppDefaultValue` `pdwCPlusTypeFlag` ; 否則，此值不相關。 在此情況下，的長度 `ppDefaultValue` 是從所指定的型別推斷而來 `pdwCPlusTypeFlag` 。  
  
 `pmdSetter`  
 擴展MethodDef token 的指標，代表屬性的 set 存取子方法。  
  
 `pmdGetter`  
 擴展MethodDef token 的指標，代表屬性的 get 存取子方法。  
  
 `rmdOtherMethod`  
 擴展MethodDef token 的陣列，表示與屬性相關聯的其他方法。  
  
 `cMax`  
 [in] `rmdOtherMethod` 陣列的大小上限。 如果您未提供夠大的陣列來容納所有方法，則會略過，而不發出警告。  
  
 `pcOtherMethod`  
 擴展中傳回的 MethodDef 權杖數目 `rmdOtherMethod` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
