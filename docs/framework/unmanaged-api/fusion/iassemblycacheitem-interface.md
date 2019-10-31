---
title: IAssemblyCacheItem 介面
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
ms.openlocfilehash: 2493b5338824e1eab3f82a9023bbcced59a98fc8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134459"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="b1862-102">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="b1862-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="b1862-103">代表全域組件快取中的單一元件。</span><span class="sxs-lookup"><span data-stu-id="b1862-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1862-104">方法</span><span class="sxs-lookup"><span data-stu-id="b1862-104">Methods</span></span>  
  
|<span data-ttu-id="b1862-105">方法</span><span class="sxs-lookup"><span data-stu-id="b1862-105">Method</span></span>|<span data-ttu-id="b1862-106">描述</span><span class="sxs-lookup"><span data-stu-id="b1862-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1862-107">AbortItem 方法</span><span class="sxs-lookup"><span data-stu-id="b1862-107">AbortItem Method</span></span>](iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="b1862-108">允許全域組件快取中的元件在釋放之前執行清除作業。</span><span class="sxs-lookup"><span data-stu-id="b1862-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="b1862-109">Commit 方法</span><span class="sxs-lookup"><span data-stu-id="b1862-109">Commit Method</span></span>](iassemblycacheitem-commit-method.md)|<span data-ttu-id="b1862-110">認可記憶體的快取元件參考。</span><span class="sxs-lookup"><span data-stu-id="b1862-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="b1862-111">CreateStream 方法</span><span class="sxs-lookup"><span data-stu-id="b1862-111">CreateStream Method</span></span>](iassemblycacheitem-createstream-method.md)|<span data-ttu-id="b1862-112">建立具有指定之名稱和格式的資料流程。</span><span class="sxs-lookup"><span data-stu-id="b1862-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1862-113">需求</span><span class="sxs-lookup"><span data-stu-id="b1862-113">Requirements</span></span>  
 <span data-ttu-id="b1862-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1862-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1862-115">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="b1862-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b1862-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1862-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1862-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1862-117">See also</span></span>

- [<span data-ttu-id="b1862-118">融合介面</span><span class="sxs-lookup"><span data-stu-id="b1862-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="b1862-119">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="b1862-119">Global Assembly Cache</span></span>](../../app-domains/gac.md)
- [<span data-ttu-id="b1862-120">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="b1862-120">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
