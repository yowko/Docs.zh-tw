---
title: IMetaDataAssemblyImport 介面
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
ms.openlocfilehash: c556fe247754b363ece0c5dc60750068276ddcc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714753"
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport 介面

提供存取及檢查組件資訊清單內容的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CloseEnum 方法](imetadataassemblyimport-closeenum-method.md)|釋放指定列舉值的控制碼。|  
|[EnumAssemblyRefs 方法](imetadataassemblyimport-enumassemblyrefs-method.md)|取得列舉值的介面指標，其中包含 `mdAssemblyRef` 目前中繼資料範圍中元件所參考之元件的標記。|  
|[EnumExportedTypes 方法](imetadataassemblyimport-enumexportedtypes-method.md)|取得列舉值的介面指標，其中包含 `mdExportedType` 目前中繼資料範圍中元件所參考之 COM 類型的標記。|  
|[EnumFiles 方法](imetadataassemblyimport-enumfiles-method.md)|取得列舉值的介面指標，其中包含 `mdFile` 目前中繼資料範圍中元件所參考之檔案的標記。|  
|[EnumManifestResources 方法](imetadataassemblyimport-enummanifestresources-method.md)|取得列舉值的介面指標，其中包含 `mdManifestResource` 目前中繼資料範圍中元件所參考之資源的標記。|  
|[FindAssembliesByName 方法](imetadataassemblyimport-findassembliesbyname-method.md)|取得 `mdAssemblyRef` 具有指定名稱之元件的標記陣列。|  
|[FindExportedTypeByName 方法](imetadataassemblyimport-findexportedtypebyname-method.md)|取得 `mdExportedType` 具有指定名稱之 COM 類型的標記。|  
|[FindManifestResourceByName 方法](imetadataassemblyimport-findmanifestresourcebyname-method.md)|取得 `mdManifestResource` 具有指定名稱之資源的權杖。|  
|[GetAssemblyFromScope 方法](imetadataassemblyimport-getassemblyfromscope-method.md)|取得目前中繼資料範圍中元件的 token。|  
|[GetAssemblyProps 方法](imetadataassemblyimport-getassemblyprops-method.md)|取得所指定元件的屬性設定。|  
|[GetAssemblyRefProps 方法](imetadataassemblyimport-getassemblyrefprops-method.md)|取得指定之標記的屬性設定 `mdAssemblyRef` 。|  
|[GetExportedTypeProps 方法](imetadataassemblyimport-getexportedtypeprops-method.md)|取得指定之 COM 類型的屬性設定。|  
|[GetFileProps 方法](imetadataassemblyimport-getfileprops-method.md)|取得指定之檔案的屬性設定。|  
|[GetManifestResourceProps 方法](imetadataassemblyimport-getmanifestresourceprops-method.md)|取得指定之資訊清單資源的屬性設定。|  
  
## <a name="requirements"></a>需求  

 **平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](metadata-interfaces.md)
- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
