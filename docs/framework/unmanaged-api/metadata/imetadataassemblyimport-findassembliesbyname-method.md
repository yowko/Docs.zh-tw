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
ms.openlocfilehash: c0f81e3767d4ea3bc336203fbe8c914b4e2bd07b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177806"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName 方法
使用通用語言運行時 （CLR） 採用的標準規則解析引用，獲取具有指定`szAssemblyName`參數的程式集陣列。  
  
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
 [在]要在其中搜索給定程式集的根目錄。 如果此值設置為`null`，`FindAssembliesByName`將僅在程式集的全域組件快取中查找。  
  
 `szPrivateBin`  
 [在]在根目錄下搜索程式集的分號分隔子目錄（例如，"bin;bin2"）的清單。 除了預設探測規則中指定的目錄外，這些目錄還被探測。  
  
 `szAssemblyName`  
 [在]要查找的程式集的名稱。 此字串的格式在 的類引用頁中<xref:System.Reflection.AssemblyName>定義。  
  
 `ppIUnk`  
 [在]放置`IMetadataAssemblyImport`介面指標的[I 未知](/cpp/atl/iunknown)類型的陣列。  
  
 `cMax`  
 [出]可放置在 中的最大介面指標數`ppIUnk`。  
  
 `pcAssemblies`  
 [出]返回的介面指標數。 也就是說，實際上放置在 中的`ppIUnk`介面指標數。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`已成功返回。|  
|`S_FALSE`|沒有程式集。|  
  
## <a name="remarks"></a>備註  
 給定程式集名稱，`FindAssembliesByName`該方法通過遵循解析程式集引用的標準規則來查找程式集。 （有關詳細資訊，請參閱[運行時如何查找程式集](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。`FindAssembliesByName`允許調用方配置程式集解析器上下文的各個方面，如應用程式庫和專用搜索路徑。  
  
 該方法`FindAssembliesByName`要求在進程中初始化 CLR，以便調用程式集解析邏輯。 因此，在調用`FindAssembliesByName`之前必須調用[Co初始化EEE（](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)傳遞COINITEE_DEFAULT），然後調用[CoUn初始化Cor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)。  
  
 `FindAssembliesByName`返回[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)指標，指向包含傳入的程式集名稱的組件資訊清單的檔。 如果未完全指定給定程式集名稱（例如，如果不包括版本），則可能會返回多個程式集。  
  
 `FindAssembliesByName`嘗試在編譯時查找引用程式集的編譯器通常使用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [執行階段如何找出組件](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
