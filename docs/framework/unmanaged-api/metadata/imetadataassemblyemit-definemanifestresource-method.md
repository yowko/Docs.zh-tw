---
title: IMetaDataAssemblyEmit::DefineManifestResource 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 026f5efe195cdb34999b65c5f47de6f68d30e11a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008125"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource 方法
為指定的資訊清單資源，建立包含其中繼資料的 `ManifestResource` 結構，並且傳回關聯的中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a>參數  
 `szName`  
 在資源的名稱。  
  
 `tkImplementation`  
 在類型為或的元資料標記 `mdtFile` `mdtAssemblyRef` ，其對應至資源提供者。 Null 值表示內嵌中繼資料的檔案是資源提供者。  
  
 `dwOffset`  
 在檔案內資源開頭的位移。 對於獨立檔案中的資源，這一律會是零。 如果資源內嵌在 PE （可移植的可執行檔）檔案中，這就是資源 BLOB 的位移，它會從 cor 標頭檔中指定的位置開始。  
  
 `dwResourceFlags`  
 在旗標值的位元組合，這個組合會指定資源定義的屬性設定。  
  
 `pmdmr`  
 脫銷傳回之元資料標記的指標。  
  
## <a name="remarks"></a>備註  
 您必須針對每個元件檔案中所實作為的 `ManifestResource` 每個資源，定義一個元資料結構。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
