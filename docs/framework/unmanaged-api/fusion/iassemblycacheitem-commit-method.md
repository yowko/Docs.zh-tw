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
ms.openlocfilehash: 5de522c00da76e7c01369c706cb7f9e2bdad4b3b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134509"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="8f24e-102">IAssemblyCacheItem::Commit 方法</span><span class="sxs-lookup"><span data-stu-id="8f24e-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="8f24e-103">認可記憶體的快取元件參考。</span><span class="sxs-lookup"><span data-stu-id="8f24e-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f24e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f24e-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f24e-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f24e-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="8f24e-106">在在融合 .idl 中定義的旗標。</span><span class="sxs-lookup"><span data-stu-id="8f24e-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="8f24e-107">[out，optional]值，指出作業的結果。</span><span class="sxs-lookup"><span data-stu-id="8f24e-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f24e-108">需求</span><span class="sxs-lookup"><span data-stu-id="8f24e-108">Requirements</span></span>  
 <span data-ttu-id="8f24e-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f24e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f24e-110">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="8f24e-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8f24e-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f24e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f24e-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="8f24e-112">See also</span></span>

- [<span data-ttu-id="8f24e-113">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="8f24e-113">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
