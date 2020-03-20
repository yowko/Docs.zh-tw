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
ms.openlocfilehash: 5aa5d78faa8ca9261594e2a649b11088e1d78ee7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177862"
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
 [在]資源的名稱。  
  
 `tkImplementation`  
 [在]類型的`mdtFile`中繼資料權杖或`mdtAssemblyRef`映射到資來源提供者的中繼資料權杖。 Null 值表示嵌入中繼資料的檔是資來源提供者。  
  
 `dwOffset`  
 [在]檔中資源開頭的偏移量。 對於獨立檔中的資源，這始終為零。 如果資源嵌入到 PE（可攜式可執行檔）檔中，這是資源 BLOB 的偏移量，它從 cor.h 標標頭檔中指定的位置開始。  
  
 `dwResourceFlags`  
 [在]指定資源定義的屬性設置的標誌值的位組合。  
  
 `pmdmr`  
 [出]指向返回的中繼資料權杖的指標。  
  
## <a name="remarks"></a>備註  
 必須`ManifestResource`為每個程式集檔中實現的每個資源定義一個元資料結構。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
