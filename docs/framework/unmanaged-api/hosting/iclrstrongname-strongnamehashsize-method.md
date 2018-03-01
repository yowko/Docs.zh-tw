---
title: "ICLRStrongName::StrongNameHashSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: acc2812567ce2d47d3f06c000fc387708c2e8acb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="78553-102">ICLRStrongName::StrongNameHashSize 方法</span><span class="sxs-lookup"><span data-stu-id="78553-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="78553-103">取得所需的雜湊，並使用指定的雜湊演算法的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="78553-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78553-104">語法</span><span class="sxs-lookup"><span data-stu-id="78553-104">Syntax</span></span>  
  
```  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78553-105">參數</span><span class="sxs-lookup"><span data-stu-id="78553-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="78553-106">[in]雜湊演算法，用來計算的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="78553-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="78553-107">[out]傳回的緩衝區大小，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="78553-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78553-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="78553-108">Return Value</span></span>  
 <span data-ttu-id="78553-109">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="78553-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78553-110">需求</span><span class="sxs-lookup"><span data-stu-id="78553-110">Requirements</span></span>  
 <span data-ttu-id="78553-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78553-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78553-112">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="78553-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="78553-113">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="78553-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78553-114">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78553-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78553-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="78553-115">See Also</span></span>  
 [<span data-ttu-id="78553-116">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="78553-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
