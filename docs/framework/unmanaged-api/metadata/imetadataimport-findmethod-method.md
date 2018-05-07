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
ms.openlocfilehash: 6b68d4e3d51fdb50290319de804a78c1a78a07a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod 方法
取得指標 methoddef 語彙基元的方法，以指定<xref:System.Type>且具有指定的名稱和中繼資料簽章。  
  
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
  
#### <a name="parameters"></a>參數  
 `td`  
 [in]`mdTypeDef`內含要搜尋之成員的類型 （類別或介面） 的語彙基元。 如果此值為`mdTokenNil`，則查閱是為全域函式。  
  
 `szName`  
 [in]若要搜尋方法的名稱。  
  
 `pvSigBlob`  
 [in]方法的二進位中繼資料簽章指標。  
  
 `cbSigBlob`  
 [in]以位元組為單位的大小`pvSigBlob`。  
  
 `pmb`  
 [out]比對的 MethodDef 語彙基元的指標。  
  
## <a name="remarks"></a>備註  
 指定封入的類別或介面的方法 (`td`)，其名稱 (`szName`)，以及 （選擇性） 其簽章 (`pvSigBlob`)。 可能會有多個具有相同名稱的類別或介面中的方法。 在此情況下，傳遞方法的簽章，以尋找唯一的符合項目。  
  
 簽章傳遞至`FindMethod`必須已產生中目前的範圍，因為簽章會繫結至特定範圍內。 簽章可以內嵌識別封入類別或實值類型的語彙基元。 語彙基元為區域 TypeDef 資料表的索引。 您無法建立在目前範圍的內容以外的執行階段簽章，並使用該簽章為輸入到輸入`FindMethod`。  
  
 `FindMethod` 尋找定義類別或介面; 中的直接的方法找不到繼承的方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Reflection.MethodInfo>  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
