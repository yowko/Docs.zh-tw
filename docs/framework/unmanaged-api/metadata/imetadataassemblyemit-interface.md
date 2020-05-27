---
title: IMetaDataAssemblyEmit 介面
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
ms.openlocfilehash: 807e1ee831a43a4ef1e7b0a269ee38131f24081e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008114"
---
# <a name="imetadataassemblyemit-interface"></a>IMetaDataAssemblyEmit 介面
提供方法，以便支援 Common Language Runtime 解析及消耗資源時所用的自我描述模型。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DefineAssembly 方法](imetadataassemblyemit-defineassembly-method.md)|為指定的組件，建立包含其中繼資料的組件資料結構，並且傳回關聯的中繼資料語彙基元。|  
|[DefineAssemblyRef 方法](imetadataassemblyemit-defineassemblyref-method.md)|為這個組件所參考的組件，建立包含其中繼資料的 `AssemblyRef` 結構，並且傳回關聯的中繼資料語彙基元。|  
|[DefineExportedType 方法](imetadataassemblyemit-defineexportedtype-method.md)|為指定的已匯出類型，建立包含其中繼資料的 `ExportedType` 結構，並且傳回關聯的中繼資料語彙基元。|  
|[DefineFile 方法](imetadataassemblyemit-definefile-method.md)|為這個組件所參考的組件，建立包含其中繼資料的 `File` 中繼資料結構，並且傳回關聯的中繼資料語彙基元。|  
|[DefineManifestResource 方法](imetadataassemblyemit-definemanifestresource-method.md)|為指定的資訊清單資源，建立包含其中繼資料的 `ManifestResource` 結構，並且傳回關聯的中繼資料語彙基元。|  
|[SetAssemblyProps 方法](imetadataassemblyemit-setassemblyprops-method.md)|修改指定的 `Assembly` 中繼資料結構。|  
|[SetAssemblyRefProps 方法](imetadataassemblyemit-setassemblyrefprops-method.md)|修改指定的 `AssemblyRef` 中繼資料結構。|  
|[SetExportedTypeProps 方法](imetadataassemblyemit-setexportedtypeprops-method.md)|修改指定的 `ExportedType` 中繼資料結構。|  
|[SetFileProps 方法](imetadataassemblyemit-setfileprops-method.md)|修改指定的 `File` 中繼資料結構。|  
|[SetManifestResourceProps 方法](imetadataassemblyemit-setmanifestresourceprops-method.md)|修改指定的 `ManifestResource` 中繼資料結構。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](metadata-interfaces.md)
- [IMetaDataAssemblyImport 介面](imetadataassemblyimport-interface.md)
