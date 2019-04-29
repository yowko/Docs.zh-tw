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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775163"
---
# <a name="corprfcodeinfo-structure"></a><span data-ttu-id="16f75-102">COR_PRF_CODE_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="16f75-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="16f75-103">代表儲存在記憶體中的一個機器碼連續區塊。</span><span class="sxs-lookup"><span data-stu-id="16f75-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16f75-104">語法</span><span class="sxs-lookup"><span data-stu-id="16f75-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="16f75-105">成員</span><span class="sxs-lookup"><span data-stu-id="16f75-105">Members</span></span>  
  
|<span data-ttu-id="16f75-106">成員</span><span class="sxs-lookup"><span data-stu-id="16f75-106">Member</span></span>|<span data-ttu-id="16f75-107">描述</span><span class="sxs-lookup"><span data-stu-id="16f75-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="16f75-108">程式碼的連續區塊的開始位址。</span><span class="sxs-lookup"><span data-stu-id="16f75-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="16f75-109">區塊大小。</span><span class="sxs-lookup"><span data-stu-id="16f75-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16f75-110">需求</span><span class="sxs-lookup"><span data-stu-id="16f75-110">Requirements</span></span>  
 <span data-ttu-id="16f75-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="16f75-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16f75-112">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="16f75-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="16f75-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16f75-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16f75-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16f75-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16f75-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16f75-115">See also</span></span>

- [<span data-ttu-id="16f75-116">分析結構</span><span class="sxs-lookup"><span data-stu-id="16f75-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
