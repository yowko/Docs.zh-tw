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
ms.openlocfilehash: a8dc09ee9f0f0fd79060bb86c599ab40a285153b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448755"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="47aed-102">CorValidatorModuleType 列舉</span><span class="sxs-lookup"><span data-stu-id="47aed-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="47aed-103">指定模組的類型。</span><span class="sxs-lookup"><span data-stu-id="47aed-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47aed-104">語法</span><span class="sxs-lookup"><span data-stu-id="47aed-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="47aed-105">Members</span><span class="sxs-lookup"><span data-stu-id="47aed-105">Members</span></span>  
  
|<span data-ttu-id="47aed-106">成員</span><span class="sxs-lookup"><span data-stu-id="47aed-106">Member</span></span>|<span data-ttu-id="47aed-107">描述</span><span class="sxs-lookup"><span data-stu-id="47aed-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="47aed-108">模組是不正確類型。</span><span class="sxs-lookup"><span data-stu-id="47aed-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="47aed-109">`CorValidatorModuleType` 列舉的最小值。</span><span class="sxs-lookup"><span data-stu-id="47aed-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="47aed-110">此模組是可移植的可執行檔（PE）。</span><span class="sxs-lookup"><span data-stu-id="47aed-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="47aed-111">模組是 .obj 檔案。</span><span class="sxs-lookup"><span data-stu-id="47aed-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="47aed-112">模組是「編輯後繼續」偵錯工具會話。</span><span class="sxs-lookup"><span data-stu-id="47aed-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="47aed-113">模組是以累加方式建立的模組。</span><span class="sxs-lookup"><span data-stu-id="47aed-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="47aed-114">`CorValidatorModuleType` 列舉的最大值。</span><span class="sxs-lookup"><span data-stu-id="47aed-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="47aed-115">需求</span><span class="sxs-lookup"><span data-stu-id="47aed-115">Requirements</span></span>  
 <span data-ttu-id="47aed-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47aed-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47aed-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="47aed-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="47aed-118">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="47aed-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="47aed-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47aed-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47aed-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47aed-120">See also</span></span>

- [<span data-ttu-id="47aed-121">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="47aed-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
