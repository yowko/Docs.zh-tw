---
title: COR_VERSION 結構
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1f0a36d186c6d9788d43b075bf9d67c36ed1acb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740563"
---
# <a name="corversion-structure"></a><span data-ttu-id="80a05-102">COR_VERSION 結構</span><span class="sxs-lookup"><span data-stu-id="80a05-102">COR_VERSION Structure</span></span>
<span data-ttu-id="80a05-103">儲存通用語言執行平台的標準四部分版本號碼。</span><span class="sxs-lookup"><span data-stu-id="80a05-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80a05-104">語法</span><span class="sxs-lookup"><span data-stu-id="80a05-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="80a05-105">成員</span><span class="sxs-lookup"><span data-stu-id="80a05-105">Members</span></span>  
  
|<span data-ttu-id="80a05-106">成員</span><span class="sxs-lookup"><span data-stu-id="80a05-106">Member</span></span>|<span data-ttu-id="80a05-107">描述</span><span class="sxs-lookup"><span data-stu-id="80a05-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="80a05-108">主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="80a05-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="80a05-109">次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="80a05-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="80a05-110">組建編號。</span><span class="sxs-lookup"><span data-stu-id="80a05-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="80a05-111">子組建編號。</span><span class="sxs-lookup"><span data-stu-id="80a05-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80a05-112">備註</span><span class="sxs-lookup"><span data-stu-id="80a05-112">Remarks</span></span>  
 <span data-ttu-id="80a05-113">如果版本號碼是 1.0.3705.288，1 是主要版本號碼、 0 是次要版本號碼、 3705 是組建編號，和 288 為子組建編號。</span><span class="sxs-lookup"><span data-stu-id="80a05-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80a05-114">需求</span><span class="sxs-lookup"><span data-stu-id="80a05-114">Requirements</span></span>  
 <span data-ttu-id="80a05-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80a05-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80a05-116">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="80a05-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="80a05-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80a05-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80a05-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80a05-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80a05-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80a05-119">See also</span></span>

- [<span data-ttu-id="80a05-120">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="80a05-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="80a05-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="80a05-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
