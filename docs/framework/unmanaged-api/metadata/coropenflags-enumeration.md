---
title: CorOpenFlags 列舉
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6999de3e1bf1da2d306cf063647b47a2be166781
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364409"
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
|`ofReadOnly`|指出應該開啟檔案進行讀取，且呼叫`QueryInterface`for [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)無法進行。|  
|`ofTakeOwnership`|表示使用的呼叫來配置的記憶體[CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) ，而且將會釋放由中繼資料。|  
|`ofNoTypeLib`|已過時。 會忽略此旗標。|  
|`ofNoTransform`|指出應停用 .winmd 檔案的自動轉換。 換言之，應停用 Windows 執行階段類型對 .NET Framework 類型的投影。 如需詳細資訊，請參閱 < [Windows 執行階段和 CLR-使用.NET 和 Windows 執行階段下面 the Hood](https://msdn.microsoft.com/magazine/jj651569.aspx)。|  
|`ofReserved1`|保留供內部使用。|  
|`ofReserved2`|保留供內部使用。|  
|`ofReserved`|保留供內部使用。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
