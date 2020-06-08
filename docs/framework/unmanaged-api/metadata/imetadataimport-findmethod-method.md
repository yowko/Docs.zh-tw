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
ms.openlocfilehash: c2ec907759a25048444ebcc81bf5bb0fd23ced58
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503649"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod 方法
取得方法之 MethodDef token 的指標，這個標記是由指定的所括住， <xref:System.Type> 且具有指定的名稱和中繼資料簽章。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 在用 `mdTypeDef` 來括住要搜尋之成員的類型（類別或介面）的 token。 如果這個值為 `mdTokenNil` ，則會針對全域函式進行查閱。  
  
 `szName`  
 在要搜尋之方法的名稱。  
  
 `pvSigBlob`  
 在方法之二進位中繼資料簽章的指標。  
  
 `cbSigBlob`  
 在的大小（以位元組為單位） `pvSigBlob` 。  
  
 `pmb`  
 脫銷相符的 MethodDef token 的指標。  
  
## <a name="remarks"></a>備註  
 您可以使用它的封入類別或介面（ `td` ）、它的名稱（） `szName` ，以及選擇性的簽章（）來指定方法 `pvSigBlob` 。 在類別或介面中，可能會有多個方法具有相同的名稱。 在此情況下，請傳遞方法的簽章，以尋找唯一的相符項。  
  
 傳遞至的簽章 `FindMethod` 必須已在目前的範圍中產生，因為簽章已系結至特定範圍。 簽章可以內嵌可識別封閉類別或實數值型別的 token。 Token 是本機 TypeDef 資料表的索引。 您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為輸入來輸入至 `FindMethod` 。  
  
 `FindMethod`只尋找直接定義于類別或介面中的方法;但找不到繼承的方法。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
