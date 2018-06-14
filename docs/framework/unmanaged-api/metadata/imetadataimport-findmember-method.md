---
title: IMetaDataImport::FindMember 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79c9a54a44ae1751cb8b1b57379ccfd6485f6e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448187"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember 方法
取得指標的 memberdef 語彙基元欄位或方法是包含所指定<xref:System.Type>且具有指定的名稱和中繼資料簽章。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a>參數  
 `td`  
 [in]類別或介面包含要搜尋之成員 TypeDef 語彙基元。 如果此值為`mdTokenNil`，查閱是為全域變數或全域函式。  
  
 `szName`  
 [in]要搜尋之成員的名稱。  
  
 `pvSigBlob`  
 [in]二進位中繼資料簽章的成員指標。  
  
 `cbSigBlob`  
 [in]以位元組為單位的大小`pvSigBlob`。  
  
 `pmb`  
 [out]比對的 MemberDef 語彙基元的指標。  
  
## <a name="remarks"></a>備註  
 指定使用其封入類別或介面的成員 (`td`)，其名稱 (`szName`)，以及 （選擇性） 其簽章 (`pvSigBlob`)。 可能會有多個成員具有相同名稱的類別或介面中。 在此情況下，傳遞成員的簽章，以尋找唯一的符合項目。  
  
 簽章傳遞至`FindMember`必須已產生中目前的範圍，因為簽章會繫結至特定範圍內。 簽章可以內嵌識別封入類別或實值類型的語彙基元。 語彙基元為區域 TypeDef 資料表的索引。 您無法建立在目前範圍的內容以外的執行階段簽章，並使用該簽章為輸入到輸入`FindMember`。  
  
 `FindMember` 尋找已直接在類別或介面中定義的成員找不到繼承的成員。  
  
> [!NOTE]
>  `FindMember` 是 helper 方法。 它會呼叫[imetadataimport:: Findmethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); 如果該呼叫找不到相符項目，`FindMember`然後呼叫[imetadataimport:: Findfield](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
