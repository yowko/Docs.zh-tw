---
title: IMetaDataAssemblyEmit::SetManifestResourceProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
ms.openlocfilehash: 74111a175b0decbc1beef7c8df5ade59d31d845b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009141"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a>IMetaDataAssemblyEmit::SetManifestResourceProps 方法
修改指定的 `ManifestResource` 中繼資料結構。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `mr`  
 在權杖，指定 `ManifestResource` 要修改的元資料結構。  
  
 `tkImplementation`  
 在`File` `AssemblyRef` 對應至資源提供者之類型或的 token。  
  
 `dwOffset`  
 在檔案內資源開頭的位移。  
  
 `dwResourceFlags`  
 在旗標值的位元組合，指定資源的屬性。  
  
## <a name="remarks"></a>備註  
 若要建立 `ManifestResource` 元資料結構，請使用[IMetaDataAssemblyEmit：:D efinemanifestresource](imetadataassemblyemit-definemanifestresource-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
