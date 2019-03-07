---
title: IMetaDataImport::FindMemberRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a58cba0ce4672a479cf5af9467d024a1b1562fc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474285"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef 方法
取得成員的 MemberRef 語彙基元的指標參考也就是加上指定<xref:System.Type>且具有指定的名稱和中繼資料簽章。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 [in]類別或介面，包含要搜尋的成員參考的 TypeRef 語彙基元。 如果此值為`mdTokenNil`，會在完成查詢的全域變數或全域函式參考。  
  
 `szName`  
 [in]若要搜尋成員參考的名稱。  
  
 `pvSigBlob`  
 [in]成員參考的二進位中繼資料簽章指標。  
  
 `cbSigBlob`  
 [in]以位元組為單位的大小`pvSigBlob`。  
  
 `pmr`  
 [out]比對的 MemberRef 語彙基元指標。  
  
## <a name="remarks"></a>備註  
 指定使用其封入類別或介面的成員 (`td`)，其名稱 (`szName`)，和 （選擇性） 其簽章 (`pvSigBlob`)。  
  
 簽章傳遞至`FindMemberRef`必須已產生在目前的範圍內，因為簽章會繫結至特定的範圍。 簽章可以內嵌識別封入類別或實值類型的語彙基元。 語彙基元是本機 TypeDef 資訊表內的索引。 您無法建置目前範圍的內容以外的執行階段簽章，並使用該簽章，做為輸入`FindMemberRef`。  
  
 `FindMemberRef` 尋找定義類別或介面中的直接成員參考找不到繼承的成員參考。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
