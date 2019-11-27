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
ms.openlocfilehash: 842d6c0deb90bc45cb59454fb30fcc3544d742f1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437947"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField 方法
取得 FieldDef token 的指標，該欄位是由指定的 <xref:System.Type> 所括住，而且具有指定的名稱和中繼資料簽章。  
  
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
 在用來括住要搜尋之欄位的類別或介面的 TypeDef token。 如果這個值是 `mdTokenNil`，就會針對全域變數進行查閱。  
  
 `szName`  
 在要搜尋之欄位的名稱。  
  
 `pvSigBlob`  
 在欄位的二進位中繼資料簽章的指標。  
  
 `cbSigBlob`  
 在`pvSigBlob`的大小（以位元組為單位）。  
  
 `pmb`  
 脫銷對應之 FieldDef token 的指標。  
  
## <a name="remarks"></a>備註  
 您可以使用其封入類別或介面（`td`）、其名稱（`szName`），以及選擇性的簽章（`pvSigBlob`）來指定欄位。  
  
 傳遞給 `FindField` 的簽章必須已在目前的範圍中產生，因為簽章已系結至特定範圍。 簽章可以內嵌可識別封閉類別或實數值型別的 token。 （Token 是本機 TypeDef 資料表的索引）。 您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為 `FindField`的輸入。  
  
 `FindField` 只會尋找直接定義于類別或介面中的欄位;它找不到繼承的欄位。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
