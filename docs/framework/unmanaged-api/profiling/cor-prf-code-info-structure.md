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
ms.openlocfilehash: b64e58a79f3dbe0c91b0c0cefc4a9d918c700cf9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718627"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="03608-102">COR_PRF_CODE_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="03608-102">COR_PRF_CODE_INFO Structure</span></span>

<span data-ttu-id="03608-103">代表儲存在記憶體中的一個機器碼連續區塊。</span><span class="sxs-lookup"><span data-stu-id="03608-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03608-104">語法</span><span class="sxs-lookup"><span data-stu-id="03608-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="03608-105">成員</span><span class="sxs-lookup"><span data-stu-id="03608-105">Members</span></span>  
  
|<span data-ttu-id="03608-106">member</span><span class="sxs-lookup"><span data-stu-id="03608-106">Member</span></span>|<span data-ttu-id="03608-107">描述</span><span class="sxs-lookup"><span data-stu-id="03608-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="03608-108">連續程式碼區塊的起始位址。</span><span class="sxs-lookup"><span data-stu-id="03608-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="03608-109">區塊的大小。</span><span class="sxs-lookup"><span data-stu-id="03608-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03608-110">需求</span><span class="sxs-lookup"><span data-stu-id="03608-110">Requirements</span></span>  

 <span data-ttu-id="03608-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03608-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03608-112">**標頭：** Corprof.h .idl</span><span class="sxs-lookup"><span data-stu-id="03608-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="03608-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03608-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03608-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03608-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03608-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03608-115">See also</span></span>

- [<span data-ttu-id="03608-116">分析結構</span><span class="sxs-lookup"><span data-stu-id="03608-116">Profiling Structures</span></span>](profiling-structures.md)
