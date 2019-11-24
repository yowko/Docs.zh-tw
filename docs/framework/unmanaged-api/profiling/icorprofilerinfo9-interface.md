---
title: ICorProfilerInfo9 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 74031fd822550f8a0752d02ce0c2d89b2f5ae546
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444958"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="a15a1-102">ICorProfilerInfo9 介面</span><span class="sxs-lookup"><span data-stu-id="a15a1-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="a15a1-103">A subclass of [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span><span class="sxs-lookup"><span data-stu-id="a15a1-103">A subclass of [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="a15a1-104">方法</span><span class="sxs-lookup"><span data-stu-id="a15a1-104">Methods</span></span>  

| <span data-ttu-id="a15a1-105">方法</span><span class="sxs-lookup"><span data-stu-id="a15a1-105">Method</span></span>|<span data-ttu-id="a15a1-106">描述</span><span class="sxs-lookup"><span data-stu-id="a15a1-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="a15a1-107">GetNativeCodeStartAddresses Method</span><span class="sxs-lookup"><span data-stu-id="a15a1-107">GetNativeCodeStartAddresses Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="a15a1-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span><span class="sxs-lookup"><span data-stu-id="a15a1-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="a15a1-109">GetILToNativeMapping3 Method</span><span class="sxs-lookup"><span data-stu-id="a15a1-109">GetILToNativeMapping3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="a15a1-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span><span class="sxs-lookup"><span data-stu-id="a15a1-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="a15a1-111">GetCodeInfo4 Method</span><span class="sxs-lookup"><span data-stu-id="a15a1-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="a15a1-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span><span class="sxs-lookup"><span data-stu-id="a15a1-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="a15a1-113">需求</span><span class="sxs-lookup"><span data-stu-id="a15a1-113">Requirements</span></span>  
<span data-ttu-id="a15a1-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="a15a1-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="a15a1-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a15a1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="a15a1-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a15a1-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a15a1-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="a15a1-117">See also</span></span>

- [<span data-ttu-id="a15a1-118">分析介面</span><span class="sxs-lookup"><span data-stu-id="a15a1-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
