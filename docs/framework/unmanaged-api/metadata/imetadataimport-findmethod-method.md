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
ms.openlocfilehash: 470b6511366cef1680eaf97f9ab376736add55c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437892"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod 方法
取得方法的 MethodDef 標記指標，此方法是由指定的 <xref:System.Type> 所括住，而且具有指定的名稱和中繼資料簽章。  
  
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
 在用來括住要搜尋之成員的類型（類別或介面）的 `mdTypeDef` token。 如果 `mdTokenNil`這個值，則會針對全域函式進行查閱。  
  
 `szName`  
 在要搜尋之方法的名稱。  
  
 `pvSigBlob`  
 在方法之二進位中繼資料簽章的指標。  
  
 `cbSigBlob`  
 在`pvSigBlob`的大小（以位元組為單位）。  
  
 `pmb`  
 脫銷相符的 MethodDef token 的指標。  
  
## <a name="remarks"></a>備註  
 您可以使用它的封入類別或介面（`td`）、其名稱（`szName`），以及選擇性的簽章（`pvSigBlob`）來指定方法。 在類別或介面中，可能會有多個方法具有相同的名稱。 在此情況下，請傳遞方法的簽章，以尋找唯一的相符項。  
  
 傳遞給 `FindMethod` 的簽章必須已在目前的範圍中產生，因為簽章已系結至特定範圍。 簽章可以內嵌可識別封閉類別或實數值型別的 token。 Token 是本機 TypeDef 資料表的索引。 您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為輸入來 `FindMethod`。  
  
 `FindMethod` 只會尋找直接定義于類別或介面中的方法;但找不到繼承的方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
