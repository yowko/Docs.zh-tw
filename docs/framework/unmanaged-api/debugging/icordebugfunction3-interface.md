---
title: ICorDebugFunction3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: 17eda7470e5f2e4b41d1f2ed164843eaeeedea93
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695865"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="bce32-102">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="bce32-102">ICorDebugFunction3 Interface</span></span>

<span data-ttu-id="bce32-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="bce32-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="bce32-104">以邏輯方式延伸 ICorDebugFunction 介面，以提供對 ReJIT 要求之程式碼的存取。</span><span class="sxs-lookup"><span data-stu-id="bce32-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bce32-105">方法</span><span class="sxs-lookup"><span data-stu-id="bce32-105">Methods</span></span>  
  
|<span data-ttu-id="bce32-106">方法</span><span class="sxs-lookup"><span data-stu-id="bce32-106">Method</span></span>|<span data-ttu-id="bce32-107">描述</span><span class="sxs-lookup"><span data-stu-id="bce32-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bce32-108">GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="bce32-108">GetActiveReJitRequestILCode Method</span></span>](icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="bce32-109">從使用中的 ReJIT 要求取得包含 IL 的 [ICorDebugILCode](icordebugilcode-interface.md) 介面指標。</span><span class="sxs-lookup"><span data-stu-id="bce32-109">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bce32-110">備註</span><span class="sxs-lookup"><span data-stu-id="bce32-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bce32-111">需求</span><span class="sxs-lookup"><span data-stu-id="bce32-111">Requirements</span></span>  

 <span data-ttu-id="bce32-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bce32-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bce32-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bce32-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bce32-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bce32-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bce32-115">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bce32-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bce32-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bce32-116">See also</span></span>

- [<span data-ttu-id="bce32-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bce32-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bce32-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="bce32-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="bce32-119">ReJIT： How-To 指南</span><span class="sxs-lookup"><span data-stu-id="bce32-119">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
