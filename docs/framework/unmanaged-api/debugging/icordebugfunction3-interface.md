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
ms.openlocfilehash: 71aa482cc2268da17f1376d8c305dd6a818d92d0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213162"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="f29b7-102">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="f29b7-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="f29b7-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="f29b7-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f29b7-104">以邏輯方式延伸 ICorDebugFunction 介面，以提供對 ReJIT 要求之程式碼的存取。</span><span class="sxs-lookup"><span data-stu-id="f29b7-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f29b7-105">方法</span><span class="sxs-lookup"><span data-stu-id="f29b7-105">Methods</span></span>  
  
|<span data-ttu-id="f29b7-106">方法</span><span class="sxs-lookup"><span data-stu-id="f29b7-106">Method</span></span>|<span data-ttu-id="f29b7-107">描述</span><span class="sxs-lookup"><span data-stu-id="f29b7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f29b7-108">GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="f29b7-108">GetActiveReJitRequestILCode Method</span></span>](icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="f29b7-109">取得[ICorDebugILCode](icordebugilcode-interface.md)的介面指標，其中包含來自作用中 ReJIT 要求的 IL。</span><span class="sxs-lookup"><span data-stu-id="f29b7-109">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f29b7-110">備註</span><span class="sxs-lookup"><span data-stu-id="f29b7-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f29b7-111">需求</span><span class="sxs-lookup"><span data-stu-id="f29b7-111">Requirements</span></span>  
 <span data-ttu-id="f29b7-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f29b7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f29b7-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f29b7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f29b7-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f29b7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f29b7-115">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f29b7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f29b7-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="f29b7-116">See also</span></span>

- [<span data-ttu-id="f29b7-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f29b7-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f29b7-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="f29b7-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="f29b7-119">ReJIT：使用說明指南</span><span class="sxs-lookup"><span data-stu-id="f29b7-119">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
