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
ms.openlocfilehash: 80623bdec939b0ae5fc13008c1c4001c613ac435
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195964"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="4288b-102">BucketParameters 結構</span><span class="sxs-lookup"><span data-stu-id="4288b-102">BucketParameters Structure</span></span>
<span data-ttu-id="4288b-103">儲存事件的型別名稱，以及與事件相關聯的目前例外狀況的參數。</span><span class="sxs-lookup"><span data-stu-id="4288b-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4288b-104">語法</span><span class="sxs-lookup"><span data-stu-id="4288b-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="4288b-105">Members</span><span class="sxs-lookup"><span data-stu-id="4288b-105">Members</span></span>  
  
|<span data-ttu-id="4288b-106">成員</span><span class="sxs-lookup"><span data-stu-id="4288b-106">Member</span></span>|<span data-ttu-id="4288b-107">描述</span><span class="sxs-lookup"><span data-stu-id="4288b-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="4288b-108">`true`，如果此結構的其餘部分有效，則為，否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="4288b-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="4288b-109">事件種類的名稱。</span><span class="sxs-lookup"><span data-stu-id="4288b-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="4288b-110">字串陣列，其中每一個都指定與事件相關聯之目前例外狀況的參數。</span><span class="sxs-lookup"><span data-stu-id="4288b-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4288b-111">需求</span><span class="sxs-lookup"><span data-stu-id="4288b-111">Requirements</span></span>  
 <span data-ttu-id="4288b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4288b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4288b-113">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="4288b-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="4288b-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4288b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4288b-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="4288b-115">See also</span></span>

- [<span data-ttu-id="4288b-116">裝載結構</span><span class="sxs-lookup"><span data-stu-id="4288b-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
