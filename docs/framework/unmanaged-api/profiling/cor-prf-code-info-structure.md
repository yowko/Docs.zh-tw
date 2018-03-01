---
title: "COR_PRF_CODE_INFO 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_PRF_CODE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODE_INFO
helpviewer_keywords:
- COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 173ebcd2b97b3b542a8ea96338a9c6b59b5dc6d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corprfcodeinfo-structure"></a><span data-ttu-id="77b96-102">COR_PRF_CODE_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="77b96-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="77b96-103">代表儲存在記憶體中的一個機器碼連續區塊。</span><span class="sxs-lookup"><span data-stu-id="77b96-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77b96-104">語法</span><span class="sxs-lookup"><span data-stu-id="77b96-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="77b96-105">成員</span><span class="sxs-lookup"><span data-stu-id="77b96-105">Members</span></span>  
  
|<span data-ttu-id="77b96-106">成員</span><span class="sxs-lookup"><span data-stu-id="77b96-106">Member</span></span>|<span data-ttu-id="77b96-107">描述</span><span class="sxs-lookup"><span data-stu-id="77b96-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="77b96-108">連續的程式碼區塊的起始位址。</span><span class="sxs-lookup"><span data-stu-id="77b96-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="77b96-109">區塊的大小。</span><span class="sxs-lookup"><span data-stu-id="77b96-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="77b96-110">需求</span><span class="sxs-lookup"><span data-stu-id="77b96-110">Requirements</span></span>  
 <span data-ttu-id="77b96-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77b96-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77b96-112">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="77b96-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="77b96-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77b96-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77b96-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77b96-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77b96-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="77b96-115">See Also</span></span>  
 [<span data-ttu-id="77b96-116">分析結構</span><span class="sxs-lookup"><span data-stu-id="77b96-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
