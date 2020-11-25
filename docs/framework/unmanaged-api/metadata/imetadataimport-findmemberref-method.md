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
ms.openlocfilehash: 0ba25c981cc389baf06ecca0db543d48ac60317b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711399"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef 方法

取得成員參考的 MemberRef 標記指標，該成員參考是由指定的所括住， <xref:System.Type> 且具有指定的名稱和中繼資料簽章。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 在用來搜尋成員參考之類別或介面的 TypeRef 標記。 如果這個值為 `mdTokenNil` ，就會針對全域變數或全域函式參考來執行查閱。  
  
 `szName`  
 在要搜尋之成員參考的名稱。  
  
 `pvSigBlob`  
 在成員參考的二進位中繼資料簽章指標。  
  
 `cbSigBlob`  
 在的大小（以位元組為單位） `pvSigBlob` 。  
  
 `pmr`  
 擴展相符的 MemberRef token 指標。  
  
## <a name="remarks"></a>備註  

 您可以使用其封入類別或介面 (`td`) 、其名稱 (`szName`) ，以及選擇性的簽章 () ，來指定成員 `pvSigBlob` 。  
  
 傳遞給的簽章 `FindMemberRef` 必須在目前的範圍內產生，因為簽章會系結至特定的範圍。 簽章可以內嵌可識別封閉類別或實數值型別的標記。 Token 是本機 TypeDef 資料表中的索引。 您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為的輸入 `FindMemberRef` 。  
  
 `FindMemberRef` 只尋找直接定義于類別或介面中的成員參考;找不到繼承的成員參考。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
