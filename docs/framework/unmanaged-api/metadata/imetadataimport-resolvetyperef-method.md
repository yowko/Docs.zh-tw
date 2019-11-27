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
ms.openlocfilehash: 800b15bb75e74898cee9d838900ea14b60620940
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431466"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef 方法
解析指定的 TypeRef 標記所表示的 <xref:System.Type> 參考。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a>參數  
 `tr`  
 在要傳回之參考型別資訊的 TypeRef 元資料標記。  
  
 `riid`  
 在要在 `ppIScope`中傳回之介面的 IID。 一般來說，這會是 IID_IMetaDataImport。  
  
 `ppIScope`  
 脫銷定義參考型別之模組範圍的介面。  
  
 `ptd`  
 脫銷表示參考型別之 TypeDef token 的指標。  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
> 如果載入多個應用程式域，請勿使用這個方法。 方法不會遵守應用程式域界限。 如果載入元件的多個版本，而且它們包含具有相同命名空間的相同類型，則方法會傳回所找到之第一個類型的模組範圍。  
  
 `ResolveTypeRef` 方法會搜尋其他模組中的型別定義。 如果找到類型定義，`ResolveTypeRef` 會傳回該模組範圍的介面，以及該類型的 TypeDef token。  
  
 如果要解析的類型參考具有 AssemblyRef 的解析範圍，則 `ResolveTypeRef` 方法只會搜尋已經使用[IMetaDataDispenser：： OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法或[IMetaDataDispenser：： OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)方法的呼叫開啟的中繼資料範圍中的相符項。 這是因為 `ResolveTypeRef` 無法只從磁片或全域組件快取中儲存元件的 AssemblyRef 範圍判斷。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
