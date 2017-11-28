---
title: "IMetaDataImport::FindField 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindField
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2178f8738ca510fb2163c1043dd94ebcb7043904
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField 方法
取得 FieldDef 語彙基元指標，會包含該欄位指定<xref:System.Type>且具有指定的名稱和中繼資料簽章。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
#### <a name="parameters"></a>參數  
 `td`  
 [in]類別或介面包含要搜尋的欄位之 TypeDef 語彙基元。 如果此值為`mdTokenNil`，查閱是為全域變數。  
  
 `szName`  
 [in]要搜尋的欄位名稱。  
  
 `pvSigBlob`  
 [in]欄位的二進位中繼資料簽章指標。  
  
 `cbSigBlob`  
 [in]以位元組為單位的大小`pvSigBlob`。  
  
 `pmb`  
 [out]比對的 FieldDef 語彙基元的指標。  
  
## <a name="remarks"></a>備註  
 您指定使用其封入類別或介面的欄位 (`td`)，其名稱 (`szName`)，以及 （選擇性） 其簽章 (`pvSigBlob`)。  
  
 簽章傳遞至`FindField`必須已產生中目前的範圍，因為簽章會繫結至特定範圍內。 簽章可以內嵌識別封入類別或實值類型的語彙基元。 （語彙基元是本機的 TypeDef 資料表的索引）。 您無法建立在目前範圍的內容以外的執行階段簽章，並使用該簽章，做為輸入`FindField`。  
  
 `FindField`尋找已直接在類別或介面中定義的欄位找不到繼承的欄位。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
