---
title: "CorValidatorModuleType 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3367f6928b5d7378b2686185ee3e03d0279cc11d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="a7c43-102">CorValidatorModuleType 列舉</span><span class="sxs-lookup"><span data-stu-id="a7c43-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="a7c43-103">指定模組的類型。</span><span class="sxs-lookup"><span data-stu-id="a7c43-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7c43-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7c43-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a><span data-ttu-id="a7c43-105">成員</span><span class="sxs-lookup"><span data-stu-id="a7c43-105">Members</span></span>  
  
|<span data-ttu-id="a7c43-106">成員</span><span class="sxs-lookup"><span data-stu-id="a7c43-106">Member</span></span>|<span data-ttu-id="a7c43-107">描述</span><span class="sxs-lookup"><span data-stu-id="a7c43-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="a7c43-108">此模組是無效的類型。</span><span class="sxs-lookup"><span data-stu-id="a7c43-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="a7c43-109">最小值`CorValidatorModuleType`列舉。</span><span class="sxs-lookup"><span data-stu-id="a7c43-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="a7c43-110">模組是可攜式執行檔 (PE) 檔。</span><span class="sxs-lookup"><span data-stu-id="a7c43-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="a7c43-111">模組是.obj 檔。</span><span class="sxs-lookup"><span data-stu-id="a7c43-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="a7c43-112">模組是 「 編輯後繼續偵錯工具工作階段。</span><span class="sxs-lookup"><span data-stu-id="a7c43-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="a7c43-113">模組是以累加方式內建的其中一個。</span><span class="sxs-lookup"><span data-stu-id="a7c43-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="a7c43-114">最大值`CorValidatorModuleType`列舉。</span><span class="sxs-lookup"><span data-stu-id="a7c43-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7c43-115">需求</span><span class="sxs-lookup"><span data-stu-id="a7c43-115">Requirements</span></span>  
 <span data-ttu-id="a7c43-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7c43-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7c43-117">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a7c43-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7c43-118">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a7c43-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7c43-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7c43-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c43-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="a7c43-120">See Also</span></span>  
 [<span data-ttu-id="a7c43-121">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="a7c43-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
