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
ms.openlocfilehash: 7626ce6b2b6278be7cd9989718c13f7c98e4ace3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="aba17-102">BucketParameters 結構</span><span class="sxs-lookup"><span data-stu-id="aba17-102">BucketParameters Structure</span></span>
<span data-ttu-id="aba17-103">儲存目前與事件相關聯的例外狀況事件和參數的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="aba17-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aba17-104">語法</span><span class="sxs-lookup"><span data-stu-id="aba17-104">Syntax</span></span>  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="aba17-105">成員</span><span class="sxs-lookup"><span data-stu-id="aba17-105">Members</span></span>  
  
|<span data-ttu-id="aba17-106">成員</span><span class="sxs-lookup"><span data-stu-id="aba17-106">Member</span></span>|<span data-ttu-id="aba17-107">說明</span><span class="sxs-lookup"><span data-stu-id="aba17-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="aba17-108">`true`如果此結構的其餘部分是有效的。否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="aba17-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="aba17-109">事件類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="aba17-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="aba17-110">字串陣列，每個皆指定與事件相關聯的目前例外狀況的參數。</span><span class="sxs-lookup"><span data-stu-id="aba17-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aba17-111">需求</span><span class="sxs-lookup"><span data-stu-id="aba17-111">Requirements</span></span>  
 <span data-ttu-id="aba17-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aba17-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aba17-113">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="aba17-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="aba17-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aba17-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aba17-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aba17-115">See Also</span></span>  
 [<span data-ttu-id="aba17-116">裝載結構</span><span class="sxs-lookup"><span data-stu-id="aba17-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
