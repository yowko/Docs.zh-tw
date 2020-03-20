---
title: IAssemblyCacheItem::Commit 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.Commit
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::Commit
helpviewer_keywords:
- IAssemblyCacheItem::Commit method [.NET Framework fusion]
- Commit method, IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: c2321f17-f46f-4815-ae41-b28678753613
topic_type:
- apiref
ms.openlocfilehash: f840438e175790a2b4c97302963b910f98dffb7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176561"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="6877a-102">IAssemblyCacheItem::Commit 方法</span><span class="sxs-lookup"><span data-stu-id="6877a-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="6877a-103">將緩存的程式集引用提交到記憶體。</span><span class="sxs-lookup"><span data-stu-id="6877a-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6877a-104">語法</span><span class="sxs-lookup"><span data-stu-id="6877a-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6877a-105">參數</span><span class="sxs-lookup"><span data-stu-id="6877a-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="6877a-106">[在]在 Fusion.idl 中定義的標誌。</span><span class="sxs-lookup"><span data-stu-id="6877a-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="6877a-107">[退出，可選]指示操作結果的值。</span><span class="sxs-lookup"><span data-stu-id="6877a-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6877a-108">需求</span><span class="sxs-lookup"><span data-stu-id="6877a-108">Requirements</span></span>  
 <span data-ttu-id="6877a-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6877a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6877a-110">**標題：** 融合.h</span><span class="sxs-lookup"><span data-stu-id="6877a-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6877a-111">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6877a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6877a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6877a-112">See also</span></span>

- [<span data-ttu-id="6877a-113">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="6877a-113">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
