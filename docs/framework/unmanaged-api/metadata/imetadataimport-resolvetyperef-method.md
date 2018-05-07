---
title: IMetaDataImport::ResolveTypeRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 106ef520f64233323cbb3f26cb3efdee152559b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef 方法
解析<xref:System.Type>指定 TypeRef 語彙基元所代表的參考。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
#### <a name="parameters"></a>參數  
 `tr`  
 [in]要傳回的參考型別資訊的 TypeRef 中繼資料語彙基元。  
  
 `riid`  
 [in]傳回介面的 IID `ppIScope`。 通常，這會是 IID_IMetaDataImport。  
  
 `ppIScope`  
 [out]要在其中定義參考的型別在模組範圍的介面。  
  
 `ptd`  
 [out]表示參考的型別 TypeDef 語彙基元的指標。  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
>  如果載入多個應用程式定義域，則不使用這個方法。 此方法不會遵守應用程式定義域界限。 如果多個版本的組件會載入，而它們包含具有相同的命名空間之相同類型，則方法會傳回模組範圍的第一個找到的類型。  
  
 `ResolveTypeRef`方法搜尋的類型定義中其他模組。 如果找到的類型定義，`ResolveTypeRef`讓介面返回該模組範圍，以及類型的 TypeDef 語彙基元。  
  
 如果要解析的型別參考已解析範圍的 AssemblyRef，`ResolveTypeRef`方法會搜尋相符項目只能在已經開啟與呼叫的中繼資料範圍[imetadatadispenser:: Openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法或[imetadatadispenser:: Openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)方法。 這是因為`ResolveTypeRef`無法判斷從範圍僅限於 AssemblyRef 磁碟上或在全域組件快取組件儲存。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
