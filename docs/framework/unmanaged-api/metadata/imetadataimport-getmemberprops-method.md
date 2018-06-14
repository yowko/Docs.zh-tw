---
title: IMetaDataImport::GetMemberProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d93763da2afbbdb1e738c802ba172e9f16e5f7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448454"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps 方法
取得中繼資料資訊，包括名稱、 二進位簽章和相對虛擬位址的<xref:System.Type>指定的中繼資料語彙基元所參考的成員。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] ULONG             *pulCodeRVA,   
   [out] DWORD             *pdwImplFlags,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `mb`  
 [in]參考成員，以取得相關聯中繼資料語彙基元。  
  
 `pClass`  
 [out]表示類別成員的中繼資料語彙基元的指標。  
  
 `szMember`  
 [out]成員的名稱。  
  
 `cchMember`  
 [in]中的寬字元大小`szMember`緩衝區。  
  
 `pchMember`  
 [out]傳回名稱的寬字元大小。  
  
 `pdwAttr`  
 [out]套用至成員的任何旗標值。  
  
 `ppvSigBlob`  
 [out]二進位中繼資料簽章的成員指標。  
  
 `pcbSigBlob`  
 [out]以位元組為單位的大小`ppvSigBlob`。  
  
 `pulCodeRVA`  
 [out]成員的相對虛擬位址指標。  
  
 `pdwImplFlags`  
 [out]成員相關聯任何方法實作旗標。  
  
 `pdwCPlusTypeFlag`  
 [out]標示旗標<xref:System.ValueType>。  
  
 `ppValue`  
 [out]這個成員所傳回的常數字串值。  
  
 `pcchValue`  
 [out]以字元為單位的大小`ppValue`，或如果`ppValue`不會保存一個字串。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
