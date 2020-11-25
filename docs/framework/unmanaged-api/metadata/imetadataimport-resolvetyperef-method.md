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
ms.openlocfilehash: 76c5519a6cd1b8994e2f869281f13d8269e89fde
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702819"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef 方法

解析 <xref:System.Type> 指定的 TypeRef 標記所表示的參考。  
  
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
 在要傳回所參考之型別資訊的 TypeRef 元資料標記。  
  
 `riid`  
 在要在其中傳回之介面的 IID `ppIScope` 。 一般來說，這會是 IID_IMetaDataImport。  
  
 `ppIScope`  
 擴展定義參考型別之模組範圍的介面。  
  
 `ptd`  
 擴展代表參考之類型的 TypeDef 標記指標。  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
> 如果載入多個應用程式域，請勿使用這個方法。 方法不遵守應用程式域界限。 如果載入元件的多個版本，而且它們包含相同的類型與相同的命名空間，則方法會傳回所找到的第一個類型的模組範圍。  
  
 `ResolveTypeRef`方法會在其他模組中搜尋型別定義。 如果找到類型定義，則會傳回 `ResolveTypeRef` 該模組範圍的介面，以及該類型的 TypeDef 標記。  
  
 如果要解析的類型參考具有 AssemblyRef 的解析範圍，此 `ResolveTypeRef` 方法只會在已使用 [IMetaDataDispenser：： OpenScope](imetadatadispenser-openscope-method.md) 方法或 [IMetaDataDispenser：： OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) 方法呼叫來開啟的中繼資料範圍內搜尋相符項。 這是因為 `ResolveTypeRef` 無法從磁片或全域組件快取中儲存元件的 AssemblyRef 範圍判斷。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
