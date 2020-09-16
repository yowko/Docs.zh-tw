---
title: ICorProfilerInfo9 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f38195b1a7983e23c7f5c20055ea8c2a8bfcb7d8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556846"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="837fb-102">ICorProfilerInfo9 介面</span><span class="sxs-lookup"><span data-stu-id="837fb-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="837fb-103">[ICorProfilerInfo8](icorprofilerinfo8-interface.md)的子類別，可提供方法來查詢具有多個機器碼版本的函式相關資訊。</span><span class="sxs-lookup"><span data-stu-id="837fb-103">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="837fb-104">方法</span><span class="sxs-lookup"><span data-stu-id="837fb-104">Methods</span></span>  

| <span data-ttu-id="837fb-105">方法</span><span class="sxs-lookup"><span data-stu-id="837fb-105">Method</span></span>|<span data-ttu-id="837fb-106">描述</span><span class="sxs-lookup"><span data-stu-id="837fb-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="837fb-107">GetNativeCodeStartAddresses 方法</span><span class="sxs-lookup"><span data-stu-id="837fb-107">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="837fb-108">在指定 functionId 和 rejitId 的情況下，列舉此程式碼目前存在的所有可編譯版本的機器碼開始位址。</span><span class="sxs-lookup"><span data-stu-id="837fb-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="837fb-109">GetILToNativeMapping3 方法</span><span class="sxs-lookup"><span data-stu-id="837fb-109">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="837fb-110">在指定機器碼起始位址的情況下，傳回此程式碼的程式碼的原生對應資訊。</span><span class="sxs-lookup"><span data-stu-id="837fb-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="837fb-111">GetCodeInfo4 方法</span><span class="sxs-lookup"><span data-stu-id="837fb-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="837fb-112">在指定機器碼起始位址的情況下，傳回儲存此程式碼的虛擬記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="837fb-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="837fb-113">需求</span><span class="sxs-lookup"><span data-stu-id="837fb-113">Requirements</span></span>  
<span data-ttu-id="837fb-114">**平臺：** 請參閱 [.Net Core 支援的作業系統](../../../core/install/windows.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="837fb-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="837fb-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="837fb-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="837fb-116">**.Net 版本：**[!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="837fb-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="837fb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="837fb-117">See also</span></span>

- [<span data-ttu-id="837fb-118">分析介面</span><span class="sxs-lookup"><span data-stu-id="837fb-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
