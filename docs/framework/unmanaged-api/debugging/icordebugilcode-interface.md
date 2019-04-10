---
title: ICorDebugILCode 介面
ms.date: 03/30/2017
api_name:
- ICorDebugILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 51c4de0c-3813-4142-be25-a85bb84efb90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 279a87039c4cbc12c7ec5f734928c851185280f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175717"
---
# <a name="icordebugilcode-interface"></a><span data-ttu-id="073dc-102">ICorDebugILCode 介面</span><span class="sxs-lookup"><span data-stu-id="073dc-102">ICorDebugILCode Interface</span></span>
<span data-ttu-id="073dc-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="073dc-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="073dc-104">代表中繼語言 (IL) 程式碼的區段。</span><span class="sxs-lookup"><span data-stu-id="073dc-104">Represents a segment of intermediate language (IL) code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="073dc-105">方法</span><span class="sxs-lookup"><span data-stu-id="073dc-105">Methods</span></span>  
  
|<span data-ttu-id="073dc-106">方法</span><span class="sxs-lookup"><span data-stu-id="073dc-106">Method</span></span>|<span data-ttu-id="073dc-107">描述</span><span class="sxs-lookup"><span data-stu-id="073dc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="073dc-108">GetEHClauses 方法</span><span class="sxs-lookup"><span data-stu-id="073dc-108">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)|<span data-ttu-id="073dc-109">傳回針對此 IL 定義之例外狀況處理 (EH) 子句清單的指標。</span><span class="sxs-lookup"><span data-stu-id="073dc-109">Returns a pointer to a list of exception handling (EH) clauses that are defined for this IL.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="073dc-110">需求</span><span class="sxs-lookup"><span data-stu-id="073dc-110">Requirements</span></span>  
 <span data-ttu-id="073dc-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="073dc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="073dc-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="073dc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="073dc-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="073dc-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="073dc-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="073dc-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="073dc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="073dc-115">See also</span></span>

- [<span data-ttu-id="073dc-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="073dc-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="073dc-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="073dc-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
