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
ms.openlocfilehash: a6c7bf332d829a440fe216756f7a23ec1277e6c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449282"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName 方法
取得具有指定的組件的陣列`szAssemblyName`使用標準的規則，用來解析參考 common language runtime (CLR) 的參數。  
  
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
  
#### <a name="parameters"></a>參數  
 `szAppBase`  
 [in]要在其中搜尋指定的組件的根目錄。 如果此值設為`null`，`FindAssembliesByName`會只能在全域組件快取中尋找組件。  
  
 `szPrivateBin`  
 [in]以分號分隔 （例如，"bin; bin2"） 下, 子目錄的根目錄，要在其中搜尋組件清單。 除了預設探查規則中指定的會探查下列目錄。  
  
 `szAssemblyName`  
 [in]若要尋找組件的名稱。 這個字串的格式定義中的類別參考頁面<xref:System.Reflection.AssemblyName>。  
  
 `ppIUnk`  
 [in]類型的陣列 <<!--zzxref:IUnknown --> `IUnknown`> 要放置`IMetadataAssemblyImport`介面指標。  
  
 `cMax`  
 [out]可以放入的介面指標的最大數目`ppIUnk`。  
  
 `pcAssemblies`  
 [out]傳回介面指標的數目。 也就是說，介面指標的數目實際置於`ppIUnk`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` 已成功傳回。|  
|`S_FALSE`|沒有組件。|  
  
## <a name="remarks"></a>備註  
 授與組件的名稱，`FindAssembliesByName`方法找到遵循標準的規則，來解析組件參考的組件。 (如需詳細資訊，請參閱[執行階段如何找出組件](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。)`FindAssembliesByName`允許呼叫端設定的組件解析程式的內容，例如應用程式基底序號和私用搜尋路徑的各種層面。  
  
 `FindAssembliesByName`方法需要 CLR 初始化程序中，才能叫用的組件解析邏輯。 因此，您必須呼叫[CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) （傳遞 COINITEE_DEFAULT） 然後再呼叫`FindAssembliesByName`，然後依照呼叫[CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)。  
  
 `FindAssembliesByName` 傳回[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)傳入的檔案包含組件名稱的組件資訊清單的指標。 如果指定的組件名稱並未完整指定 （例如，如果它不包含版本），可能會傳回多個組件。  
  
 `FindAssembliesByName` 通常會嘗試尋找參考的組件，在編譯時期編譯器使用。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [執行階段如何找出組件](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
