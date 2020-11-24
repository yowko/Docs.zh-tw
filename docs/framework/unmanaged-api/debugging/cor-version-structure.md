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
ms.openlocfilehash: 874c0520482cc5a3bbfcdd17924edee84fe91ff5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675317"
---
# <a name="cor_version-structure"></a><span data-ttu-id="bd23a-102">COR_VERSION 結構</span><span class="sxs-lookup"><span data-stu-id="bd23a-102">COR_VERSION Structure</span></span>

<span data-ttu-id="bd23a-103">儲存通用語言執行平台的標準四部分版本號碼。</span><span class="sxs-lookup"><span data-stu-id="bd23a-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd23a-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd23a-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="bd23a-105">成員</span><span class="sxs-lookup"><span data-stu-id="bd23a-105">Members</span></span>  
  
|<span data-ttu-id="bd23a-106">member</span><span class="sxs-lookup"><span data-stu-id="bd23a-106">Member</span></span>|<span data-ttu-id="bd23a-107">描述</span><span class="sxs-lookup"><span data-stu-id="bd23a-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="bd23a-108">主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="bd23a-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="bd23a-109">次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="bd23a-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="bd23a-110">組建編號。</span><span class="sxs-lookup"><span data-stu-id="bd23a-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="bd23a-111">子組建編號。</span><span class="sxs-lookup"><span data-stu-id="bd23a-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd23a-112">備註</span><span class="sxs-lookup"><span data-stu-id="bd23a-112">Remarks</span></span>  

 <span data-ttu-id="bd23a-113">如果版本號碼是1.0.3705.288，1是主要版本號碼，0是次要版本號碼，3705是組建編號，而288是子組建編號。</span><span class="sxs-lookup"><span data-stu-id="bd23a-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd23a-114">需求</span><span class="sxs-lookup"><span data-stu-id="bd23a-114">Requirements</span></span>  

 <span data-ttu-id="bd23a-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd23a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd23a-116">**標頭：** Cordebug.h .idl</span><span class="sxs-lookup"><span data-stu-id="bd23a-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="bd23a-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd23a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd23a-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd23a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd23a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd23a-119">See also</span></span>

- [<span data-ttu-id="bd23a-120">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="bd23a-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="bd23a-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="bd23a-121">Debugging</span></span>](index.md)
