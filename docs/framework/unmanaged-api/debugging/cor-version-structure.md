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
ms.openlocfilehash: cc9a67e16635209c3bf303e97dc3e5938943a653
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099084"
---
# <a name="cor_version-structure"></a><span data-ttu-id="fc217-102">COR_VERSION 結構</span><span class="sxs-lookup"><span data-stu-id="fc217-102">COR_VERSION Structure</span></span>
<span data-ttu-id="fc217-103">儲存通用語言執行平台的標準四部分版本號碼。</span><span class="sxs-lookup"><span data-stu-id="fc217-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc217-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc217-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="fc217-105">Members</span><span class="sxs-lookup"><span data-stu-id="fc217-105">Members</span></span>  
  
|<span data-ttu-id="fc217-106">成員</span><span class="sxs-lookup"><span data-stu-id="fc217-106">Member</span></span>|<span data-ttu-id="fc217-107">描述</span><span class="sxs-lookup"><span data-stu-id="fc217-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="fc217-108">主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="fc217-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="fc217-109">次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="fc217-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="fc217-110">組建編號。</span><span class="sxs-lookup"><span data-stu-id="fc217-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="fc217-111">子組建編號。</span><span class="sxs-lookup"><span data-stu-id="fc217-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc217-112">備註</span><span class="sxs-lookup"><span data-stu-id="fc217-112">Remarks</span></span>  
 <span data-ttu-id="fc217-113">如果版本號碼是1.0.3705.288，1是主要版本號碼，0是次要版本號碼，3705是組建編號，288則是子組建編號。</span><span class="sxs-lookup"><span data-stu-id="fc217-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc217-114">需求</span><span class="sxs-lookup"><span data-stu-id="fc217-114">Requirements</span></span>  
 <span data-ttu-id="fc217-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc217-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc217-116">**標頭：** Cordebug.h .idl</span><span class="sxs-lookup"><span data-stu-id="fc217-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="fc217-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc217-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc217-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc217-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc217-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="fc217-119">See also</span></span>

- [<span data-ttu-id="fc217-120">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="fc217-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="fc217-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="fc217-121">Debugging</span></span>](index.md)
