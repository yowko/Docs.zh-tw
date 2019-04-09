---
title: CorValidatorModuleType 列舉
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14eee096c25967d321e4693b260501827d944a80
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154176"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="f542d-102">CorValidatorModuleType 列舉</span><span class="sxs-lookup"><span data-stu-id="f542d-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="f542d-103">指定模組的類型。</span><span class="sxs-lookup"><span data-stu-id="f542d-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f542d-104">語法</span><span class="sxs-lookup"><span data-stu-id="f542d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f542d-105">成員</span><span class="sxs-lookup"><span data-stu-id="f542d-105">Members</span></span>  
  
|<span data-ttu-id="f542d-106">成員</span><span class="sxs-lookup"><span data-stu-id="f542d-106">Member</span></span>|<span data-ttu-id="f542d-107">描述</span><span class="sxs-lookup"><span data-stu-id="f542d-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="f542d-108">此模組是無效的類型。</span><span class="sxs-lookup"><span data-stu-id="f542d-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="f542d-109">最小值`CorValidatorModuleType`列舉。</span><span class="sxs-lookup"><span data-stu-id="f542d-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="f542d-110">此模組是可攜式執行檔 (PE) 檔案。</span><span class="sxs-lookup"><span data-stu-id="f542d-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="f542d-111">此模組是.obj 檔。</span><span class="sxs-lookup"><span data-stu-id="f542d-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="f542d-112">此模組是編輯後繼續偵錯工具工作階段。</span><span class="sxs-lookup"><span data-stu-id="f542d-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="f542d-113">此模組是以累加方式內建的其中一個。</span><span class="sxs-lookup"><span data-stu-id="f542d-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="f542d-114">最大值`CorValidatorModuleType`列舉。</span><span class="sxs-lookup"><span data-stu-id="f542d-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f542d-115">需求</span><span class="sxs-lookup"><span data-stu-id="f542d-115">Requirements</span></span>  
 <span data-ttu-id="f542d-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f542d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f542d-117">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f542d-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f542d-118">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f542d-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f542d-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="f542d-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f542d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f542d-120">See also</span></span>

- [<span data-ttu-id="f542d-121">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="f542d-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
