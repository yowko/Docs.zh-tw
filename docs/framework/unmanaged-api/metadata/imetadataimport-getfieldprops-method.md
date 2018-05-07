---
title: IMetaDataImport::GetFieldProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04b6c04868efff31253b2d723c5783060382212b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps 方法
取得與指定 FieldDef 語彙基元所參考欄位相關聯的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `mb`  
 [in]FieldDef 語彙基元，代表要取得相關聯的中繼資料的欄位。  
  
 `pClass`  
 [out]表示欄位所屬的類別類型的 TypeDef 語彙基元指標。  
  
 `szField`  
 [out]欄位的名稱。  
  
 `cchField`  
 [in]寬字元的緩衝區大小*szField*。  
  
 `pchField`  
 [out]實際傳回的緩衝區大小。  
  
 `pdwAttr`  
 [out]欄位的中繼資料與相關聯的旗標。  
  
 `ppvSigBlob`  
 [in]描述欄位的二進位中繼資料值的指標。  
  
 `pcbSigBlob`  
 [out]以位元組為單位的大小`ppvSigBlob`。  
  
 `pdwCPlusTypeFlag`  
 [out]指定欄位的值類型的旗標。  
  
 `ppValue`  
 [out]欄位的常值。  
  
 `pcchValue`  
 [out]以字元為單位的大小`ppValue`，或為零，如果字串不存在。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
