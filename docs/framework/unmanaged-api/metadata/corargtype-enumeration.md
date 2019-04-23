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
ms.openlocfilehash: af9ca932a4c4a12a2c89571f40162a4ecbd5c33d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144491"
---
# <a name="corargtype-enumeration"></a><span data-ttu-id="261a0-102">CorArgType 列舉</span><span class="sxs-lookup"><span data-stu-id="261a0-102">CorArgType Enumeration</span></span>
<span data-ttu-id="261a0-103">包含值，這些值描述執行階段控制代碼的原生類型。</span><span class="sxs-lookup"><span data-stu-id="261a0-103">Contains values that describe the native type of a runtime handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="261a0-104">語法</span><span class="sxs-lookup"><span data-stu-id="261a0-104">Syntax</span></span>  
  
```  
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
  
## <a name="requirements"></a><span data-ttu-id="261a0-105">需求</span><span class="sxs-lookup"><span data-stu-id="261a0-105">Requirements</span></span>  
 <span data-ttu-id="261a0-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="261a0-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="261a0-107">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="261a0-107">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="261a0-108">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="261a0-108">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="261a0-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="261a0-109">See also</span></span>

- [<span data-ttu-id="261a0-110">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="261a0-110">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
