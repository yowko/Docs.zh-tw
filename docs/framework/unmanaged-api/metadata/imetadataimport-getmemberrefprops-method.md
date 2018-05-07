---
title: IMetaDataImport::GetMemberRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d62b9be1bef16014e2870c15a232bb46d4daf10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetmemberrefprops-method"></a>IMetaDataImport::GetMemberRefProps 方法
取得與指定語彙基元所參考成員相關聯的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,   
   [out] mdToken           *ptk,   
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pbSig   
);  
```  
  
#### <a name="parameters"></a>參數  
 `mr`  
 [in]要傳回相關聯的中繼資料的 MemberRef 語彙基元。  
  
 `ptk`  
 [out]TypeDef 或 TypeRef 或 TypeSpec 語彙基元表示宣告成員或表示模組類別宣告成員或代表該成員是 MethodDef ModuleRef 語彙基元的類別。  
  
 `szMember`  
 [out]成員的名稱的的字串緩衝區。  
  
 `cchMember`  
 [in]要求的大小，以寬字元`szMember`。  
  
 `pchMember`  
 [out]傳回的大小的寬字元`szMember`。  
  
 `ppvSibBlob`  
 [out]成員的二進位中繼資料簽章指標。  
  
 `pbSig`  
 [out]以位元組為單位的大小`ppvSigBlob`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
