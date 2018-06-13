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
ms.openlocfilehash: 97e9ae5a7c35b4f9b6e2b4ca7e754b5b7480dfa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444135"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="f23b7-102">CorValidatorModuleType 列舉</span><span class="sxs-lookup"><span data-stu-id="f23b7-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="f23b7-103">指定模組的類型。</span><span class="sxs-lookup"><span data-stu-id="f23b7-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f23b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="f23b7-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f23b7-105">成員</span><span class="sxs-lookup"><span data-stu-id="f23b7-105">Members</span></span>  
  
|<span data-ttu-id="f23b7-106">成員</span><span class="sxs-lookup"><span data-stu-id="f23b7-106">Member</span></span>|<span data-ttu-id="f23b7-107">描述</span><span class="sxs-lookup"><span data-stu-id="f23b7-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="f23b7-108">此模組是無效的類型。</span><span class="sxs-lookup"><span data-stu-id="f23b7-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="f23b7-109">最小值`CorValidatorModuleType`列舉。</span><span class="sxs-lookup"><span data-stu-id="f23b7-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="f23b7-110">模組是可攜式執行檔 (PE) 檔。</span><span class="sxs-lookup"><span data-stu-id="f23b7-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="f23b7-111">模組是.obj 檔。</span><span class="sxs-lookup"><span data-stu-id="f23b7-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="f23b7-112">模組是 「 編輯後繼續偵錯工具工作階段。</span><span class="sxs-lookup"><span data-stu-id="f23b7-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="f23b7-113">模組是以累加方式內建的其中一個。</span><span class="sxs-lookup"><span data-stu-id="f23b7-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="f23b7-114">最大值`CorValidatorModuleType`列舉。</span><span class="sxs-lookup"><span data-stu-id="f23b7-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f23b7-115">需求</span><span class="sxs-lookup"><span data-stu-id="f23b7-115">Requirements</span></span>  
 <span data-ttu-id="f23b7-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f23b7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f23b7-117">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f23b7-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f23b7-118">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f23b7-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f23b7-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f23b7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f23b7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f23b7-120">See Also</span></span>  
 [<span data-ttu-id="f23b7-121">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="f23b7-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
