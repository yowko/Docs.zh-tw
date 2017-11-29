---
title: "CorManifestResourceFlags 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorManifestResourceFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorManifestResourceFlags
helpviewer_keywords: CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5cdaba8b1186d1720ff8b64f50a8effc4691fe8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="c9345-102">CorManifestResourceFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="c9345-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="c9345-103">表示資源的組件資訊清單中編碼的可見性。</span><span class="sxs-lookup"><span data-stu-id="c9345-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9345-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9345-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c9345-105">成員</span><span class="sxs-lookup"><span data-stu-id="c9345-105">Members</span></span>  
  
|<span data-ttu-id="c9345-106">成員</span><span class="sxs-lookup"><span data-stu-id="c9345-106">Member</span></span>|<span data-ttu-id="c9345-107">說明</span><span class="sxs-lookup"><span data-stu-id="c9345-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="c9345-108">保留的。</span><span class="sxs-lookup"><span data-stu-id="c9345-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="c9345-109">資源為公用。</span><span class="sxs-lookup"><span data-stu-id="c9345-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="c9345-110">資源是私用。</span><span class="sxs-lookup"><span data-stu-id="c9345-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9345-111">需求</span><span class="sxs-lookup"><span data-stu-id="c9345-111">Requirements</span></span>  
 <span data-ttu-id="c9345-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9345-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9345-113">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c9345-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c9345-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9345-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9345-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9345-115">See Also</span></span>  
 [<span data-ttu-id="c9345-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="c9345-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
