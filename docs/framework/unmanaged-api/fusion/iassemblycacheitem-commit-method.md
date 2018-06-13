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
ms.openlocfilehash: 6f5cbb7c0b4e3ce6d66d30e812008fc3419d7d7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429088"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="b98d8-102">IAssemblyCacheItem::Commit 方法</span><span class="sxs-lookup"><span data-stu-id="b98d8-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="b98d8-103">認可記憶體的快取的組件參考。</span><span class="sxs-lookup"><span data-stu-id="b98d8-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b98d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="b98d8-104">Syntax</span></span>  
  
```  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b98d8-105">參數</span><span class="sxs-lookup"><span data-stu-id="b98d8-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="b98d8-106">[in]支援下列值： 旗標。</span><span class="sxs-lookup"><span data-stu-id="b98d8-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="b98d8-107">[out，optional]值，指出作業的結果。</span><span class="sxs-lookup"><span data-stu-id="b98d8-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b98d8-108">需求</span><span class="sxs-lookup"><span data-stu-id="b98d8-108">Requirements</span></span>  
 <span data-ttu-id="b98d8-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b98d8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b98d8-110">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b98d8-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b98d8-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b98d8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b98d8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b98d8-112">See Also</span></span>  
 [<span data-ttu-id="b98d8-113">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="b98d8-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
