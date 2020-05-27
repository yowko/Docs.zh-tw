---
title: CorFileFlags 列舉
ms.date: 03/30/2017
api_name:
- CorFileFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileFlags
helpviewer_keywords:
- CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type:
- apiref
ms.openlocfilehash: c8c2757e99b80204ad52e69a596d62c55c369965
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007412"
---
# <a name="corfileflags-enumeration"></a>CorFileFlags 列舉
包含值，描述在[IMetaDataAssemblyEmit：:D efinefile](imetadataassemblyemit-definefile-method.md)的呼叫中所定義的檔案類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`ffContainsMetaData`|表示檔案不是資源檔。|  
|`ffContainsNoMetaData`|指出檔案（可能是資源檔）不包含中繼資料。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
