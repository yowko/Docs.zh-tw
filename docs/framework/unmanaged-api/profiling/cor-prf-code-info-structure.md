---
title: COR_PRF_CODE_INFO 結構
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 56734a9971759b78a835917c4914cf55edaa47a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103281"
---
# <a name="corprfcodeinfo-structure"></a><span data-ttu-id="3c8a3-102">COR_PRF_CODE_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="3c8a3-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="3c8a3-103">代表儲存在記憶體中的一個機器碼連續區塊。</span><span class="sxs-lookup"><span data-stu-id="3c8a3-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c8a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c8a3-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="3c8a3-105">成員</span><span class="sxs-lookup"><span data-stu-id="3c8a3-105">Members</span></span>  
  
|<span data-ttu-id="3c8a3-106">成員</span><span class="sxs-lookup"><span data-stu-id="3c8a3-106">Member</span></span>|<span data-ttu-id="3c8a3-107">描述</span><span class="sxs-lookup"><span data-stu-id="3c8a3-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="3c8a3-108">程式碼的連續區塊的開始位址。</span><span class="sxs-lookup"><span data-stu-id="3c8a3-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="3c8a3-109">區塊大小。</span><span class="sxs-lookup"><span data-stu-id="3c8a3-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c8a3-110">需求</span><span class="sxs-lookup"><span data-stu-id="3c8a3-110">Requirements</span></span>  
 <span data-ttu-id="3c8a3-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c8a3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c8a3-112">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3c8a3-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3c8a3-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c8a3-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3c8a3-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="3c8a3-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3c8a3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c8a3-115">See also</span></span>

- [<span data-ttu-id="3c8a3-116">分析結構</span><span class="sxs-lookup"><span data-stu-id="3c8a3-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
