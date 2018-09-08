---
title: ICLRStrongName::StrongNameHashSize 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c09832d296033b0790d3e6282763a1163abdfd2
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130454"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="5a6e3-102">ICLRStrongName::StrongNameHashSize 方法</span><span class="sxs-lookup"><span data-stu-id="5a6e3-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="5a6e3-103">使用指定的雜湊演算法取得雜湊所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="5a6e3-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a6e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a6e3-104">Syntax</span></span>  
  
```  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a6e3-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a6e3-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="5a6e3-106">[in]雜湊演算法，用來計算的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="5a6e3-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="5a6e3-107">[out]傳回的緩衝區大小，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="5a6e3-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a6e3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="5a6e3-108">Return Value</span></span>  
 <span data-ttu-id="5a6e3-109">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="5a6e3-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a6e3-110">需求</span><span class="sxs-lookup"><span data-stu-id="5a6e3-110">Requirements</span></span>  
 <span data-ttu-id="5a6e3-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a6e3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a6e3-112">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5a6e3-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5a6e3-113">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5a6e3-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a6e3-114">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a6e3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a6e3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a6e3-115">See Also</span></span>  
 [<span data-ttu-id="5a6e3-116">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="5a6e3-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
