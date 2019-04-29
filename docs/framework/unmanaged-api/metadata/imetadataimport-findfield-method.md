---
title: IMetaDataImport::FindField 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 88cd08b4290739808079bc8ecb713a5c5ea96584
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777893"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField 方法
取得指標 FieldDef 語彙基元的欄位，以指定<xref:System.Type>且具有指定的名稱和中繼資料簽章。  
  
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
  
## <a name="parameters"></a>參數  
 `td`  
 [in]類別或介面，包含要搜尋的欄位之 TypeDef 語彙基元。 如果此值為`mdTokenNil`，會在完成查詢的全域變數。  
  
 `szName`  
 [in]要搜尋的欄位名稱。  
  
 `pvSigBlob`  
 [in]二進位中繼資料簽章欄位的指標。  
  
 `cbSigBlob`  
 [in]以位元組為單位的大小`pvSigBlob`。  
  
 `pmb`  
 [out]比對的 FieldDef 語彙基元指標。  
  
## <a name="remarks"></a>備註  
 指定使用其封入類別或介面的欄位 (`td`)，其名稱 (`szName`)，和 （選擇性） 其簽章 (`pvSigBlob`)。  
  
 簽章傳遞至`FindField`必須已產生在目前的範圍內，因為簽章會繫結至特定的範圍。 簽章可以內嵌識別封入類別或實值類型的語彙基元。 （語彙基元，為區域 TypeDef 資訊表內的索引）。 您無法建置目前範圍的內容以外的執行階段簽章，並使用該簽章，做為輸入`FindField`。  
  
 `FindField` 尋找直接在類別或介面中所定義的欄位找不到繼承的欄位。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
