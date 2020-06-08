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
ms.openlocfilehash: 11ea6e468909ea42e38bdc7b76c60c460c98025e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503662"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField 方法
取得欄位的 FieldDef token 指標，此標記是由指定的所括住， <xref:System.Type> 且具有指定的名稱和中繼資料簽章。  
  
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
 在用來括住要搜尋之欄位的類別或介面的 TypeDef token。 如果這個值為 `mdTokenNil` ，則會針對全域變數進行查閱。  
  
 `szName`  
 在要搜尋之欄位的名稱。  
  
 `pvSigBlob`  
 在欄位的二進位中繼資料簽章的指標。  
  
 `cbSigBlob`  
 在的大小（以位元組為單位） `pvSigBlob` 。  
  
 `pmb`  
 脫銷對應之 FieldDef token 的指標。  
  
## <a name="remarks"></a>備註  
 您可以使用其封入類別或介面（ `td` ）、其名稱（） `szName` ，以及選擇性的簽章（）來指定欄位 `pvSigBlob` 。  
  
 傳遞至的簽章 `FindField` 必須已在目前的範圍中產生，因為簽章已系結至特定範圍。 簽章可以內嵌可識別封閉類別或實數值型別的 token。 （Token 是本機 TypeDef 資料表的索引）。 您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為的輸入 `FindField` 。  
  
 `FindField`只尋找直接定義于類別或介面中的欄位;它找不到繼承的欄位。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
