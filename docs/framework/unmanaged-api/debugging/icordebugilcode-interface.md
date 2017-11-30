---
title: "ICorDebugILCode 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILCode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 51c4de0c-3813-4142-be25-a85bb84efb90
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 22be32839c5a083502a4cf0507269b3aae0619c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilcode-interface"></a><span data-ttu-id="91fad-102">ICorDebugILCode 介面</span><span class="sxs-lookup"><span data-stu-id="91fad-102">ICorDebugILCode Interface</span></span>
<span data-ttu-id="91fad-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="91fad-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="91fad-104">代表中繼語言 (IL) 程式碼的區段。</span><span class="sxs-lookup"><span data-stu-id="91fad-104">Represents a segment of intermediate language (IL) code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91fad-105">方法</span><span class="sxs-lookup"><span data-stu-id="91fad-105">Methods</span></span>  
  
|<span data-ttu-id="91fad-106">方法</span><span class="sxs-lookup"><span data-stu-id="91fad-106">Method</span></span>|<span data-ttu-id="91fad-107">說明</span><span class="sxs-lookup"><span data-stu-id="91fad-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91fad-108">GetEHClauses 方法</span><span class="sxs-lookup"><span data-stu-id="91fad-108">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)|<span data-ttu-id="91fad-109">傳回針對此 IL 定義之例外狀況處理 (EH) 子句清單的指標。</span><span class="sxs-lookup"><span data-stu-id="91fad-109">Returns a pointer to a list of exception handling (EH) clauses that are defined for this IL.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91fad-110">需求</span><span class="sxs-lookup"><span data-stu-id="91fad-110">Requirements</span></span>  
 <span data-ttu-id="91fad-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91fad-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91fad-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91fad-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91fad-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91fad-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91fad-114">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91fad-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91fad-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91fad-115">See Also</span></span>  
 [<span data-ttu-id="91fad-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="91fad-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="91fad-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="91fad-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
