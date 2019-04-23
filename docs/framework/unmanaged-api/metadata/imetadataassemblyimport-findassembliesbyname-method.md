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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b388dae0f109ff366f83c92de99b00b80bcc01a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108715"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName 方法
取得具有指定的組件的陣列`szAssemblyName`參數，用來解析參考的 common language runtime (CLR) 所採用的標準規則。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]要在其中搜尋指定的組件的根目錄。 如果此值設為`null`，`FindAssembliesByName`會尋找只在全域組件快取中組件。  
  
 `szPrivateBin`  
 [in]以分號分隔 （例如，「 bin; bin2"） 下, 子目錄的根目錄，在其中搜尋組件清單。 除了預設探查規則中所指定會探查下列目錄。  
  
 `szAssemblyName`  
 [in]若要尋找組件的名稱。 此字串的格式定義的類別參考頁面<xref:System.Reflection.AssemblyName>。  
  
 `ppIUnk`  
 [in]類型的陣列[IUnknown](/cpp/atl/iunknown)要放入`IMetadataAssemblyImport`介面指標。  
  
 `cMax`  
 [out]可以放在的介面指標的最大數目`ppIUnk`。  
  
 `pcAssemblies`  
 [out]傳回的介面指標的數目。 也就是介面指標的數目實際放在`ppIUnk`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` 已成功傳回。|  
|`S_FALSE`|沒有組件。|  
  
## <a name="remarks"></a>備註  
 授與組件的名稱，`FindAssembliesByName`方法會遵循標準的規則，以便解析組件參考來尋找組件。 (如需詳細資訊，請參閱 <<c0> [ 執行階段如何找出組件](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。)`FindAssembliesByName`允許呼叫端設定的組件解析程式的內容，例如應用程式基底和私用的搜尋路徑的各種層面。  
  
 `FindAssembliesByName`方法需要 CLR 初始化程序中，才能叫用組件解析邏輯。 因此，您必須呼叫[CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) （傳遞 COINITEE_DEFAULT） 然後再呼叫`FindAssembliesByName`，然後依照呼叫[CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)。  
  
 `FindAssembliesByName` 會傳回[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)傳入的檔案包含組件名稱的組件資訊清單的指標。 如果指定的組件名稱完全未指定 （例如，如果它不包含版本），可能會傳回多個組件。  
  
 `FindAssembliesByName` 通常會使用嘗試尋找參考的組件在編譯時期的編譯器。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [執行階段如何找出組件](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
