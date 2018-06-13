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
ms.openlocfilehash: bac5578caaf5682c12509b41da77b3d7cca76312
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415229"
---
# <a name="icordebugilcode-interface"></a><span data-ttu-id="6bee3-102">ICorDebugILCode 介面</span><span class="sxs-lookup"><span data-stu-id="6bee3-102">ICorDebugILCode Interface</span></span>
<span data-ttu-id="6bee3-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="6bee3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6bee3-104">代表中繼語言 (IL) 程式碼的區段。</span><span class="sxs-lookup"><span data-stu-id="6bee3-104">Represents a segment of intermediate language (IL) code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bee3-105">方法</span><span class="sxs-lookup"><span data-stu-id="6bee3-105">Methods</span></span>  
  
|<span data-ttu-id="6bee3-106">方法</span><span class="sxs-lookup"><span data-stu-id="6bee3-106">Method</span></span>|<span data-ttu-id="6bee3-107">描述</span><span class="sxs-lookup"><span data-stu-id="6bee3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6bee3-108">GetEHClauses 方法</span><span class="sxs-lookup"><span data-stu-id="6bee3-108">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)|<span data-ttu-id="6bee3-109">傳回針對此 IL 定義之例外狀況處理 (EH) 子句清單的指標。</span><span class="sxs-lookup"><span data-stu-id="6bee3-109">Returns a pointer to a list of exception handling (EH) clauses that are defined for this IL.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6bee3-110">需求</span><span class="sxs-lookup"><span data-stu-id="6bee3-110">Requirements</span></span>  
 <span data-ttu-id="6bee3-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6bee3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bee3-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bee3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bee3-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bee3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bee3-114">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bee3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bee3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bee3-115">See Also</span></span>  
 [<span data-ttu-id="6bee3-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6bee3-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6bee3-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="6bee3-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
