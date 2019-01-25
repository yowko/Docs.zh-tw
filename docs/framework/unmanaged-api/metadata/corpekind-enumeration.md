---
title: CorPEKind 列舉
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ab94bf7c55d4c19a4f3672ed86808575b8a2239
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536905"
---
# <a name="corpekind-enumeration"></a>CorPEKind 列舉
包含值，描述可移植執行檔 (PE) 檔案，從呼叫傳回[IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`peNot`|指出這不是 PE 檔案。|  
|`peILOnly`|表示此 PE 檔包含只受管理的程式碼。|  
|`pe32BitRequired`|指出此 PE 檔會 Win32 呼叫。|  
|`pe32Plus`|表示在 64 位元平台上執行此 PE 檔。|  
|`pe32Unmanaged`|指出此 PE 檔案是原生程式碼。|  
|pe32BitPreferred|指出此 PE 檔是平台相關，而且偏好在 32 位元環境中載入。|  
  
## <a name="remarks"></a>備註  
 這些值可用以位元的組合。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
