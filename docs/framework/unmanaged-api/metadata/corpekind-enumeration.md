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
ms.openlocfilehash: b5869eb16bd768d58a6f27a83f2d8d51914a8aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443111"
---
# <a name="corpekind-enumeration"></a>CorPEKind 列舉
包含描述可攜式執行檔 (PE)，值傳回呼叫[imetadataimport2:: Getpekind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)。  
  
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
|`peNot`|指出這不是 PE 檔。|  
|`peILOnly`|表示此 PE 檔包含只受管理的程式碼。|  
|`pe32BitRequired`|指出此 PE 檔案，會呼叫 Win32。|  
|`pe32Plus`|表示在 64 位元平台上執行此 PE 檔。|  
|`pe32Unmanaged`|表示此 PE 檔是原生程式碼。|  
|pe32BitPreferred|指出此 PE 檔案是平台限制，而且偏好在 32 位元環境中載入。|  
  
## <a name="remarks"></a>備註  
 以位元的組合，可以使用這些值。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
