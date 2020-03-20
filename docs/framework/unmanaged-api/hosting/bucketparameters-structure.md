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
ms.openlocfilehash: 4d9de489bdeb0ab506f56ff08f4afb4cf6d0ab4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178280"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="03a1b-102">BucketParameters 結構</span><span class="sxs-lookup"><span data-stu-id="03a1b-102">BucketParameters Structure</span></span>
<span data-ttu-id="03a1b-103">存儲事件的類型名稱以及與事件關聯的當前異常的參數。</span><span class="sxs-lookup"><span data-stu-id="03a1b-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03a1b-104">語法</span><span class="sxs-lookup"><span data-stu-id="03a1b-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="03a1b-105">成員</span><span class="sxs-lookup"><span data-stu-id="03a1b-105">Members</span></span>  
  
|<span data-ttu-id="03a1b-106">member</span><span class="sxs-lookup"><span data-stu-id="03a1b-106">Member</span></span>|<span data-ttu-id="03a1b-107">描述</span><span class="sxs-lookup"><span data-stu-id="03a1b-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="03a1b-108">`true`，如果此結構的其餘部分有效;如果此結構的其餘部分有效，則為否則， `false`.</span><span class="sxs-lookup"><span data-stu-id="03a1b-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="03a1b-109">事件種類的名稱。</span><span class="sxs-lookup"><span data-stu-id="03a1b-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="03a1b-110">字串陣列，每個字串都指定與事件關聯的當前異常的參數。</span><span class="sxs-lookup"><span data-stu-id="03a1b-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03a1b-111">需求</span><span class="sxs-lookup"><span data-stu-id="03a1b-111">Requirements</span></span>  
 <span data-ttu-id="03a1b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03a1b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03a1b-113">**標題：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="03a1b-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="03a1b-114">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03a1b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a1b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03a1b-115">See also</span></span>

- [<span data-ttu-id="03a1b-116">裝載結構</span><span class="sxs-lookup"><span data-stu-id="03a1b-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
