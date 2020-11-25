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
ms.openlocfilehash: 3729f06097fa4dce6de009307183d5e97c24479b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728299"
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
 在 `mdtFile` 或 `mdtAssemblyRef` 對應至資源提供者之類型的元資料標記。 Null 值表示內嵌中繼資料的檔案是資源提供者。  
  
 `dwOffset`  
 在檔案內資源開頭的位移。 針對獨立檔案中的資源，這一律會是零。 如果資源內嵌于 PE (可攜式可執行檔) 檔案中，這就是資源 BLOB 的位移，它會從 cor .h 標頭檔中指定的位置開始。  
  
 `dwResourceFlags`  
 在旗標值的位元組合，這些值會指定資源定義的屬性設定。  
  
 `pmdmr`  
 擴展傳回之元資料標記的指標。  
  
## <a name="remarks"></a>備註  

 您 `ManifestResource` 必須為每個元件檔案中所執行的每個資源定義一個元資料結構。  
  
## <a name="requirements"></a>需求  

 **平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
