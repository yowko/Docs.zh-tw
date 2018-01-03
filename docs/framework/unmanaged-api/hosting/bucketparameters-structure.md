---
title: "BucketParameters 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: BucketParameters
api_location: mscoree.dll
api_type: COM
f1_keywords: BucketParameters
helpviewer_keywords: BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9db30133a01877c6ae048b9152f35b066219aa22
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="c1dc6-102">BucketParameters 結構</span><span class="sxs-lookup"><span data-stu-id="c1dc6-102">BucketParameters Structure</span></span>
<span data-ttu-id="c1dc6-103">儲存目前與事件相關聯的例外狀況事件和參數的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c1dc6-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1dc6-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1dc6-104">Syntax</span></span>  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="c1dc6-105">成員</span><span class="sxs-lookup"><span data-stu-id="c1dc6-105">Members</span></span>  
  
|<span data-ttu-id="c1dc6-106">成員</span><span class="sxs-lookup"><span data-stu-id="c1dc6-106">Member</span></span>|<span data-ttu-id="c1dc6-107">描述</span><span class="sxs-lookup"><span data-stu-id="c1dc6-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="c1dc6-108">`true`如果此結構的其餘部分是有效的。否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="c1dc6-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="c1dc6-109">事件類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="c1dc6-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="c1dc6-110">字串陣列，每個皆指定與事件相關聯的目前例外狀況的參數。</span><span class="sxs-lookup"><span data-stu-id="c1dc6-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c1dc6-111">需求</span><span class="sxs-lookup"><span data-stu-id="c1dc6-111">Requirements</span></span>  
 <span data-ttu-id="c1dc6-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c1dc6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1dc6-113">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="c1dc6-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c1dc6-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1dc6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1dc6-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="c1dc6-115">See Also</span></span>  
 [<span data-ttu-id="c1dc6-116">裝載結構</span><span class="sxs-lookup"><span data-stu-id="c1dc6-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
