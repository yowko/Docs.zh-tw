---
title: IMetaDataAssemblyImport::FindAssembliesByName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: 05902436c09d082f90af01f48c7e918650317ce7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009414"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName 方法
`szAssemblyName`使用 common language runtime （CLR）用來解析參考的標準規則，取得具有指定參數的元件陣列。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,
    [in]  LPCWSTR     szPrivateBin,
    [in]  LPCWSTR     szAssemblyName,
    [out] IUnknown    *ppIUnk[],
    [in]  ULONG       cMax,
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a>參數  
 `szAppBase`  
 在要在其中搜尋指定元件的根目錄。 如果這個值設定為 `null` ， `FindAssembliesByName` 則只會查看元件的全域組件快取。  
  
 `szPrivateBin`  
 在根目錄底下以分號分隔的子目錄清單（例如，"bin; bin2"），在該目錄中會搜尋元件。 除了預設探查規則中指定的目錄以外，還會探查這些目錄。  
  
 `szAssemblyName`  
 在要尋找之元件的名稱。 這個字串的格式定義于的 [類別參考] 頁面中 <xref:System.Reflection.AssemblyName> 。  
  
 `ppIUnk`  
 在[IUnknown](/cpp/atl/iunknown)類型的陣列，要在其中放置 `IMetadataAssemblyImport` 介面指標。  
  
 `cMax`  
 脫銷可以放入的介面指標的最大數目 `ppIUnk` 。  
  
 `pcAssemblies`  
 脫銷傳回的介面指標數目。 也就是，實際放入的介面指標數目 `ppIUnk` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`已成功傳回。|  
|`S_FALSE`|沒有任何元件。|  
  
## <a name="remarks"></a>備註  
 在指定元件名稱的 `FindAssembliesByName` 情況下，方法會依照解析元件參考的標準規則來尋找元件。 （如需詳細資訊，請參閱[執行時間如何找出元件](../../deployment/how-the-runtime-locates-assemblies.md)）。`FindAssembliesByName`可讓呼叫者設定元件解析程式內容的各種層面，例如應用程式基底和私用搜尋路徑。  
  
 方法需要在進程中初始化 CLR，才能叫用 `FindAssembliesByName` 元件解析邏輯。 因此，在呼叫之前，您必須呼叫[CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) （傳遞 COINITEE_DEFAULT）， `FindAssembliesByName` 然後遵循[CoUninitializeCor](../hosting/couninitializecor-function.md)的呼叫。  
  
 `FindAssembliesByName`傳回檔案的[IMetaDataImport](imetadataimport-interface.md)指標，此檔案包含傳入之元件名稱的組件資訊清單。 如果未完整指定給定的元件名稱（例如，如果它不包含版本），則可能會傳回多個元件。  
  
 `FindAssembliesByName`編譯器常用於嘗試在編譯時期尋找參考元件的編譯器。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [執行階段如何找出組件](../../deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport 介面](imetadataassemblyimport-interface.md)
