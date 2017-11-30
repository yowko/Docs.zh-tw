---
title: "COR_VERSION 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_VERSION
helpviewer_keywords: COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bd4a878b51685befb39eb486097be2e2f2c1d409
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="corversion-structure"></a><span data-ttu-id="b7ad9-102">COR_VERSION 結構</span><span class="sxs-lookup"><span data-stu-id="b7ad9-102">COR_VERSION Structure</span></span>
<span data-ttu-id="b7ad9-103">儲存通用語言執行平台的標準四部分版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b7ad9-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7ad9-104">語法</span><span class="sxs-lookup"><span data-stu-id="b7ad9-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="b7ad9-105">成員</span><span class="sxs-lookup"><span data-stu-id="b7ad9-105">Members</span></span>  
  
|<span data-ttu-id="b7ad9-106">成員</span><span class="sxs-lookup"><span data-stu-id="b7ad9-106">Member</span></span>|<span data-ttu-id="b7ad9-107">說明</span><span class="sxs-lookup"><span data-stu-id="b7ad9-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="b7ad9-108">主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b7ad9-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="b7ad9-109">次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b7ad9-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="b7ad9-110">組建編號。</span><span class="sxs-lookup"><span data-stu-id="b7ad9-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="b7ad9-111">子組建編號。</span><span class="sxs-lookup"><span data-stu-id="b7ad9-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7ad9-112">備註</span><span class="sxs-lookup"><span data-stu-id="b7ad9-112">Remarks</span></span>  
 <span data-ttu-id="b7ad9-113">如果版本號碼是 1.0.3705.288，1 是主要版本號碼，0 是次要版本號碼、 3705 是組建編號，而 288 是次組建編號。</span><span class="sxs-lookup"><span data-stu-id="b7ad9-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7ad9-114">需求</span><span class="sxs-lookup"><span data-stu-id="b7ad9-114">Requirements</span></span>  
 <span data-ttu-id="b7ad9-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7ad9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7ad9-116">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="b7ad9-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="b7ad9-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7ad9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7ad9-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7ad9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ad9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7ad9-119">See Also</span></span>  
 [<span data-ttu-id="b7ad9-120">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="b7ad9-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="b7ad9-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="b7ad9-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
