---
title: CorArgType 列舉
ms.date: 03/30/2017
api_name:
- CorArgType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorArgType
helpviewer_keywords:
- CorArgType enumeration [.NET Framework metadata]
ms.assetid: 3c1cb268-57a0-4664-91c7-f6908ff29e32
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ae7b61d056c08691e19e639353b6ab6fb8443c6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780937"
---
# <a name="corargtype-enumeration"></a><span data-ttu-id="1b855-102">CorArgType 列舉</span><span class="sxs-lookup"><span data-stu-id="1b855-102">CorArgType Enumeration</span></span>
<span data-ttu-id="1b855-103">包含值，這些值描述執行階段控制代碼的原生類型。</span><span class="sxs-lookup"><span data-stu-id="1b855-103">Contains values that describe the native type of a runtime handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b855-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b855-104">Syntax</span></span>  
  
```cpp  
typedef enum CorArgType {  
  
    IMAGE_CEE_CS_END        = 0x0,  
    IMAGE_CEE_CS_VOID       = 0x1,  
    IMAGE_CEE_CS_I4         = 0x2,  
    IMAGE_CEE_CS_I8         = 0x3,  
    IMAGE_CEE_CS_R4         = 0x4,  
    IMAGE_CEE_CS_R8         = 0x5,  
    IMAGE_CEE_CS_PTR        = 0x6,  
    IMAGE_CEE_CS_OBJECT     = 0x7,  
    IMAGE_CEE_CS_STRUCT4    = 0x8,  
    IMAGE_CEE_CS_STRUCT32   = 0x9,  
    IMAGE_CEE_CS_BYVALUE    = 0xA  
  
} CorArgType;  
```  
  
## <a name="requirements"></a><span data-ttu-id="1b855-105">需求</span><span class="sxs-lookup"><span data-stu-id="1b855-105">Requirements</span></span>  
 <span data-ttu-id="1b855-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b855-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b855-107">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="1b855-107">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1b855-108">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b855-108">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b855-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b855-109">See also</span></span>

- [<span data-ttu-id="1b855-110">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="1b855-110">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
