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
ms.openlocfilehash: 9b42f0f7c8e2878ee3ec140344f51517a24247c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729859"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField 方法

取得欄位的 FieldDef token 指標，該欄位是由指定 <xref:System.Type> 且具有指定的名稱和中繼資料簽章的欄位所括住。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 在包含要搜尋之欄位的類別或介面的 TypeDef 標記。 如果這個值為 `mdTokenNil` ，就會針對全域變數進行查閱。  
  
 `szName`  
 在要搜尋之欄位的名稱。  
  
 `pvSigBlob`  
 在欄位的二進位中繼資料簽章指標。  
  
 `cbSigBlob`  
 在的大小（以位元組為單位） `pvSigBlob` 。  
  
 `pmb`  
 擴展相符 FieldDef token 的指標。  
  
## <a name="remarks"></a>備註  

 您可以使用其封入類別或介面 (`td`) 、其名稱 (`szName`) ，以及選擇性的簽章 () ，來指定欄位 `pvSigBlob` 。  
  
 傳遞給的簽章 `FindField` 必須在目前的範圍內產生，因為簽章會系結至特定的範圍。 簽章可以內嵌可識別封閉類別或實數值型別的標記。  (權杖是) 的本機 TypeDef 資料表的索引。 您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為的輸入 `FindField` 。  
  
 `FindField` 只尋找直接在類別或介面中定義的欄位;找不到繼承的欄位。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
