---
title: "COR_PRF_FUNCTION_ARGUMENT_RANGE 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords: COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c0dd9cac695d892c07f33728c22bd35102c4389
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="38c5f-102">COR_PRF_FUNCTION_ARGUMENT_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="38c5f-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="38c5f-103">代表記憶體中由左至右連續儲存的函式引數區塊。</span><span class="sxs-lookup"><span data-stu-id="38c5f-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38c5f-104">語法</span><span class="sxs-lookup"><span data-stu-id="38c5f-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="38c5f-105">成員</span><span class="sxs-lookup"><span data-stu-id="38c5f-105">Members</span></span>  
  
|<span data-ttu-id="38c5f-106">Members</span><span class="sxs-lookup"><span data-stu-id="38c5f-106">Members</span></span>|<span data-ttu-id="38c5f-107">說明</span><span class="sxs-lookup"><span data-stu-id="38c5f-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="38c5f-108">區塊的起始位址。</span><span class="sxs-lookup"><span data-stu-id="38c5f-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="38c5f-109">此連續區塊的長度。</span><span class="sxs-lookup"><span data-stu-id="38c5f-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38c5f-110">需求</span><span class="sxs-lookup"><span data-stu-id="38c5f-110">Requirements</span></span>  
 <span data-ttu-id="38c5f-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38c5f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38c5f-112">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="38c5f-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="38c5f-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38c5f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38c5f-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38c5f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38c5f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38c5f-115">See Also</span></span>  
 [<span data-ttu-id="38c5f-116">分析結構</span><span class="sxs-lookup"><span data-stu-id="38c5f-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
