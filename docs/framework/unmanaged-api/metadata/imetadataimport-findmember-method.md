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
ms.openlocfilehash: 4eefb7ec1e7d0d130ec64531a59d1d5bbce04963
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968925"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember 方法
取得欄位或方法的 MemberDef token 指標, 此標記是由指定<xref:System.Type>的所括住, 且具有指定的名稱和中繼資料簽章。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 在用來括住要搜尋之成員的類別或介面的 TypeDef token。 如果這個值為`mdTokenNil`, 則會針對全域變數或全域函式進行查閱。  
  
 `szName`  
 在要搜尋之成員的名稱。  
  
 `pvSigBlob`  
 在成員的二進位中繼資料簽章的指標。  
  
 `cbSigBlob`  
 在的`pvSigBlob`大小 (以位元組為單位)。  
  
 `pmb`  
 脫銷對應之 MemberDef token 的指標。  
  
## <a name="remarks"></a>備註  
 您可以使用其封入類別或介面 (`td`)、其名稱 (`szName`), 以及選擇性的簽章 (`pvSigBlob`) 來指定成員。 類別或介面中可能有多個具有相同名稱的成員。 在此情況下, 請傳遞成員的簽章來尋找唯一的相符項。  
  
 傳遞至`FindMember`的簽章必須已在目前的範圍中產生, 因為簽章已系結至特定範圍。 簽章可以內嵌可識別封閉類別或實數值型別的 token。 Token 是本機 TypeDef 資料表的索引。 您無法在目前範圍的內容之外建立執行時間簽章, 並使用該簽章做為輸入來輸入`FindMember`至。  
  
 `FindMember`只尋找直接定義于類別或介面中的成員;它找不到繼承的成員。  
  
> [!NOTE]
> `FindMember`是 helper 方法。 它會呼叫[IMetaDataImport:: FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md);如果該呼叫找不到相符的, `FindMember`則會呼叫[IMetaDataImport:: FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
