---
title: IMetaDataImport::FindMethod 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28aa8313e7ba0c071187d0f1f6d78431b16fc005
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164797"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod 方法
取得指標的 MethodDef 語彙基元的方法，以指定<xref:System.Type>且具有指定的名稱和中繼資料簽章。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 [in]`mdTypeDef`括住要搜尋之成員的類型 （類別或介面） 的語彙基元。 如果此值為`mdTokenNil`，則會在完成查詢的全域函式。  
  
 `szName`  
 [in]要搜尋的方法名稱。  
  
 `pvSigBlob`  
 [in]二進位中繼資料簽章方法的指標。  
  
 `cbSigBlob`  
 [in]以位元組為單位的大小`pvSigBlob`。  
  
 `pmb`  
 [out]比對的 MethodDef 語彙基元指標。  
  
## <a name="remarks"></a>備註  
 指定使用其封入類別或介面的方法 (`td`)，其名稱 (`szName`)，和 （選擇性） 其簽章 (`pvSigBlob`)。 可能有多個具有相同名稱的類別或介面中的方法。 在此情況下，傳遞方法的簽章，以尋找唯一相符項目。  
  
 簽章傳遞至`FindMethod`必須已產生在目前的範圍內，因為簽章會繫結至特定的範圍。 簽章可以內嵌識別封入類別或實值類型的語彙基元。 語彙基元是本機 TypeDef 資訊表內的索引。 您無法建置目前範圍的內容以外的執行階段簽章，並使用該簽章為輸入至輸入`FindMethod`。  
  
 `FindMethod` 尋找直接在類別或介面中所定義的方法找不到繼承的方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
