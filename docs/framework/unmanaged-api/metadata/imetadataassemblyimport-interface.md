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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da75f98edb54080658dc86f48d4ebb458d72f20d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport 介面
提供存取及檢查組件資訊清單內容的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CloseEnum 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|釋放的控制代碼指定的列舉值。|  
|[EnumAssemblyRefs 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|取得列舉值，其中包含的介面指標`mdAssemblyRef`目前中繼資料範圍內組件所參考的組件的語彙基元。|  
|[EnumExportedTypes 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|取得列舉值，其中包含的介面指標`mdExportedType`目前中繼資料範圍內的組件所參考的 COM 類型的語彙基元。|  
|[EnumFiles 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|取得列舉值，其中包含的介面指標`mdFile`檔案目前的中繼資料範圍內組件參考語彙基元。|  
|[EnumManifestResources 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|取得列舉值，其中包含的介面指標`mdManifestResource`語彙基元所參考的資源目前的中繼資料範圍中的組件。|  
|[FindAssembliesByName 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|取得陣列的`mdAssemblyRef`語彙基元的指定名稱的組件。|  
|[FindExportedTypeByName 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|取得`mdExportedType`具有指定名稱的 COM 類型的語彙基元。|  
|[FindManifestResourceByName 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|取得`mdManifestResource`語彙基元的指定名稱的資源。|  
|[GetAssemblyFromScope 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|取得目前中繼資料範圍內組件的語彙基元。|  
|[GetAssemblyProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|取得指定的組件的屬性設定。|  
|[GetAssemblyRefProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|取得指定的屬性設定`mdAssemblyRef`語彙基元。|  
|[GetExportedTypeProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|取得指定的 COM 類型的屬性設定。|  
|[GetFileProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|取得指定之檔案的屬性設定。|  
|[GetManifestResourceProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|取得指定的資訊清單資源的屬性設定。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
