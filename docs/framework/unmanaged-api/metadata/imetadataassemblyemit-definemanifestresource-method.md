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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 145659e8761b8c7804faf25e47a280a9d4f874b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679028"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource 方法
為指定的資訊清單資源，建立包含其中繼資料的 `ManifestResource` 結構，並且傳回關聯的中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `szName`  
 [in]資源的名稱。  
  
 `tkImplementation`  
 [in]型別的中繼資料語彙基元`mdtFile`或`mdtAssemblyRef`子可對應到資源提供者。 NULL 值表示在其中內嵌中繼資料檔案是資源提供者。  
  
 `dwOffset`  
 [in]資源檔中的開始位移。 如需獨立檔案中的資源，這一律為零。 如果資源內嵌 PE （可攜式執行檔） 中，這會是資源的 BLOB，cor.h 標頭檔中指定的位置開始的位移。  
  
 `dwResourceFlags`  
 [in]指定資源定義的屬性設定的旗標值的位元組合。  
  
 `pmdmr`  
 [out]傳回的中繼資料語彙基元指標。  
  
## <a name="remarks"></a>備註  
 一個`ManifestResource`必須定義在每個組件的檔案中實作每個資源的中繼資料結構。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
