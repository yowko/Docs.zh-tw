---
title: "CorParamAttr 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorParamAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorParamAttr
helpviewer_keywords: CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 469c148dbce4139a3d72021991185f3ed6f7c5da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corparamattr-enumeration"></a>CorParamAttr 列舉
包含值，這些值描述方法參數的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`pdIn`|指定的參數會傳遞至方法呼叫。|  
|`pdOut`|指定的參數傳遞從方法傳回。|  
|`pdOptional`|指定是選擇性參數。|  
|`pdReservedMask`|保留供內部使用的 common language runtime。|  
|`pdHasDefault`|指定參數有預設值。|  
|`pdHasFieldMarshal`|指定的參數有封送處理資訊。|  
|`pdUnused`|未使用。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
