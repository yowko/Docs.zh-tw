---
title: "CorOpenFlags 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorOpenFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorOpenFlags
helpviewer_keywords: CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4447f648277576169c9004d1880283728639c8f3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="coropenflags-enumeration"></a>CorOpenFlags 列舉
包含在開啟資訊清單檔案時控制中繼資料行為的旗標值。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`ofRead`|指出應將檔案開啟為僅供讀取。|  
|`ofWrite`|指出應將檔案開啟為可供寫入。<br /><br /> 若您在開啟 .winmd 檔案時使用 `ofWrite` 旗標，也應該傳遞 `ofNoTransform` 旗標。|  
|`ofReadWriteMask`|讀取及寫入的遮罩。|  
|`ofCopyMemory`|指出應將檔案讀取至記憶體。 中繼資料應保留其自己的複本。|  
|`ofCacheImage`|已過時。 會忽略此旗標。|  
|`ofManifestMetadata`|已過時。 會忽略此旗標。|  
|`ofReadOnly`|指出應該開啟檔案進行讀取，且呼叫`QueryInterface`如[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)無法進行。|  
|`ofTakeOwnership`|指出使用的呼叫配置的記憶體[CoTaskMemAlloc](http://msdn.microsoft.com/library/c4cb588d-9482-4f90-a92e-75b604540d5c)和中繼資料，將會釋放。|  
|`ofNoTypeLib`|已過時。 會忽略此旗標。|  
|`ofNoTransform`|指出應停用 .winmd 檔案的自動轉換。 換言之，應停用 Windows 執行階段類型對 .NET Framework 類型的投影。 如需詳細資訊，請參閱[.NET 和 Windows 執行階段與下面其實](http://msdn.microsoft.com/magazine/jj651569.aspx)。|  
|`ofReserved1`|保留供內部使用。|  
|`ofReserved2`|保留供內部使用。|  
|`ofReserved`|保留供內部使用。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
