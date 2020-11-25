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
ms.openlocfilehash: 111e42a6d8f413c616779bc44e0722ab38781588
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711334"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod 方法

取得方法的 MethodDef 標記指標，該方法包含由指定的 <xref:System.Type> ，且具有指定的名稱和中繼資料簽章。  
  
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
 在 `mdTypeDef` 類型的標記 (類別或介面) ，其中包含要搜尋的成員。 如果這個值為 `mdTokenNil` ，則會對全域函式進行查閱。  
  
 `szName`  
 在要搜尋之方法的名稱。  
  
 `pvSigBlob`  
 在方法的二進位中繼資料簽章指標。  
  
 `cbSigBlob`  
 在的大小（以位元組為單位） `pvSigBlob` 。  
  
 `pmb`  
 擴展相符的 MethodDef token 指標。  
  
## <a name="remarks"></a>備註  

 您可以使用其封入類別或介面 (`td`) 、其名稱 (`szName`) ，以及選擇性的簽章 () ，來指定方法 `pvSigBlob` 。 類別或介面中可能會有多個相同名稱的方法。 在此情況下，請傳遞方法的簽章，以找出唯一的相符項。  
  
 傳遞給的簽章 `FindMethod` 必須在目前的範圍內產生，因為簽章會系結至特定的範圍。 簽章可以內嵌可識別封閉類別或實數值型別的標記。 Token 是本機 TypeDef 資料表中的索引。 您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為輸入的輸入 `FindMethod` 。  
  
 `FindMethod` 只尋找直接在類別或介面中定義的方法;但找不到繼承的方法。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
