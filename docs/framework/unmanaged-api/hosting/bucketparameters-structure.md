---
title: BucketParameters 結構
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
ms.openlocfilehash: 8b54cb30ec96ad0fb7851af6f2d465fe771886ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677847"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="6466d-102">BucketParameters 結構</span><span class="sxs-lookup"><span data-stu-id="6466d-102">BucketParameters Structure</span></span>

<span data-ttu-id="6466d-103">儲存事件的類型名稱，以及與事件相關聯之目前例外狀況的參數。</span><span class="sxs-lookup"><span data-stu-id="6466d-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6466d-104">語法</span><span class="sxs-lookup"><span data-stu-id="6466d-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="6466d-105">成員</span><span class="sxs-lookup"><span data-stu-id="6466d-105">Members</span></span>  
  
|<span data-ttu-id="6466d-106">member</span><span class="sxs-lookup"><span data-stu-id="6466d-106">Member</span></span>|<span data-ttu-id="6466d-107">描述</span><span class="sxs-lookup"><span data-stu-id="6466d-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="6466d-108">`true`如果此結構的其餘部分是有效的，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="6466d-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="6466d-109">事件種類的名稱。</span><span class="sxs-lookup"><span data-stu-id="6466d-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="6466d-110">字串的陣列，其中每一個都指定與事件相關聯之目前例外狀況的參數。</span><span class="sxs-lookup"><span data-stu-id="6466d-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6466d-111">需求</span><span class="sxs-lookup"><span data-stu-id="6466d-111">Requirements</span></span>  

 <span data-ttu-id="6466d-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6466d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6466d-113">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6466d-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="6466d-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6466d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6466d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6466d-115">See also</span></span>

- [<span data-ttu-id="6466d-116">裝載結構</span><span class="sxs-lookup"><span data-stu-id="6466d-116">Hosting Structures</span></span>](hosting-structures.md)
