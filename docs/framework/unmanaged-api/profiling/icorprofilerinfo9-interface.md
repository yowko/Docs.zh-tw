---
title: ICorProfilerInfo9 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: af6bd02c6d4e88c72dca20d2520d1ecc8cf1c421
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928791"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="3e002-102">ICorProfilerInfo9 介面</span><span class="sxs-lookup"><span data-stu-id="3e002-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="3e002-103">[ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)的子類別，提供方法來查詢具有多個機器碼版本之函數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3e002-103">A subclass of [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="3e002-104">方法</span><span class="sxs-lookup"><span data-stu-id="3e002-104">Methods</span></span>  

| <span data-ttu-id="3e002-105">方法</span><span class="sxs-lookup"><span data-stu-id="3e002-105">Method</span></span>|<span data-ttu-id="3e002-106">描述</span><span class="sxs-lookup"><span data-stu-id="3e002-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="3e002-107">GetNativeCodeStartAddresses 方法</span><span class="sxs-lookup"><span data-stu-id="3e002-107">GetNativeCodeStartAddresses Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="3e002-108">假設有 functionId 和 rejitId，會列舉此程式碼中所有目前存在之已編譯版本的原生程式碼起始位址。</span><span class="sxs-lookup"><span data-stu-id="3e002-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="3e002-109">GetILToNativeMapping3 方法</span><span class="sxs-lookup"><span data-stu-id="3e002-109">GetILToNativeMapping3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="3e002-110">假設機器碼的起始位址，會傳回這個程式碼編譯版本的原生到 IL 對應資訊。</span><span class="sxs-lookup"><span data-stu-id="3e002-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="3e002-111">GetCodeInfo4 方法</span><span class="sxs-lookup"><span data-stu-id="3e002-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="3e002-112">假設機器碼的起始位址，會傳回儲存此程式碼的虛擬記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="3e002-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="3e002-113">需求</span><span class="sxs-lookup"><span data-stu-id="3e002-113">Requirements</span></span>  
<span data-ttu-id="3e002-114">**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。</span><span class="sxs-lookup"><span data-stu-id="3e002-114">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
<span data-ttu-id="3e002-115">**標頭：** Corprof.idl .idl，Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="3e002-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="3e002-116">**.Net 版本：** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e002-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3e002-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e002-117">See also</span></span>

- [<span data-ttu-id="3e002-118">分析介面</span><span class="sxs-lookup"><span data-stu-id="3e002-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
