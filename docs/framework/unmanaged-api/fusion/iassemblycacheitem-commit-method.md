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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3757eee4c013ccf4f0f6d21ef64a92a5ffd70f19
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074309"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="20188-102">IAssemblyCacheItem::Commit 方法</span><span class="sxs-lookup"><span data-stu-id="20188-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="20188-103">認可記憶體的快取的組件參考。</span><span class="sxs-lookup"><span data-stu-id="20188-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20188-104">語法</span><span class="sxs-lookup"><span data-stu-id="20188-104">Syntax</span></span>  
  
```  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20188-105">參數</span><span class="sxs-lookup"><span data-stu-id="20188-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="20188-106">[in]支援下列值： 旗標。</span><span class="sxs-lookup"><span data-stu-id="20188-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="20188-107">[out，optional]值，指出作業的結果。</span><span class="sxs-lookup"><span data-stu-id="20188-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20188-108">需求</span><span class="sxs-lookup"><span data-stu-id="20188-108">Requirements</span></span>  
 <span data-ttu-id="20188-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="20188-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20188-110">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="20188-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="20188-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20188-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20188-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20188-112">See also</span></span>

- [<span data-ttu-id="20188-113">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="20188-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
