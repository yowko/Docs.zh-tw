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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5998ce684726b2386d8f1e05eb7eaeccf455747c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110452"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="f13ee-102">BucketParameters 結構</span><span class="sxs-lookup"><span data-stu-id="f13ee-102">BucketParameters Structure</span></span>
<span data-ttu-id="f13ee-103">儲存目前的例外狀況與事件相關聯的事件和參數的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="f13ee-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f13ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="f13ee-104">Syntax</span></span>  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="f13ee-105">成員</span><span class="sxs-lookup"><span data-stu-id="f13ee-105">Members</span></span>  
  
|<span data-ttu-id="f13ee-106">成員</span><span class="sxs-lookup"><span data-stu-id="f13ee-106">Member</span></span>|<span data-ttu-id="f13ee-107">描述</span><span class="sxs-lookup"><span data-stu-id="f13ee-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|`true`<span data-ttu-id="f13ee-108">如果此結構的其餘部分會有效;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="f13ee-108">, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="f13ee-109">事件類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="f13ee-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="f13ee-110">字串陣列，其中每一個指定事件相關聯的目前例外狀況的參數。</span><span class="sxs-lookup"><span data-stu-id="f13ee-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f13ee-111">需求</span><span class="sxs-lookup"><span data-stu-id="f13ee-111">Requirements</span></span>  
 <span data-ttu-id="f13ee-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f13ee-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f13ee-113">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="f13ee-113">**Header:** MSCorEE.idl</span></span>  
  
 **<span data-ttu-id="f13ee-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="f13ee-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f13ee-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f13ee-115">See also</span></span>

- [<span data-ttu-id="f13ee-116">裝載結構</span><span class="sxs-lookup"><span data-stu-id="f13ee-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
