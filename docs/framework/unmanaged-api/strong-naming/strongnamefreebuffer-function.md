---
title: StrongNameFreeBuffer 函式
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bfc6491a1d18c81a44a7d9c5084f744c9b76281
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072568"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="6a47e-102">StrongNameFreeBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="6a47e-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="6a47e-103">釋放使用對強式名稱函式 (例如 [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)、[StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md) 或 [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)) 的上一個呼叫所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="6a47e-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="6a47e-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="6a47e-104">This function has been deprecated.</span></span> <span data-ttu-id="6a47e-105">使用[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="6a47e-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a47e-106">語法</span><span class="sxs-lookup"><span data-stu-id="6a47e-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a47e-107">參數</span><span class="sxs-lookup"><span data-stu-id="6a47e-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="6a47e-108">[in]要釋放的記憶體指標。</span><span class="sxs-lookup"><span data-stu-id="6a47e-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a47e-109">需求</span><span class="sxs-lookup"><span data-stu-id="6a47e-109">Requirements</span></span>  
 <span data-ttu-id="6a47e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a47e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a47e-111">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6a47e-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6a47e-112">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6a47e-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="6a47e-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="6a47e-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6a47e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a47e-114">See also</span></span>

- [<span data-ttu-id="6a47e-115">StrongNameFreeBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="6a47e-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="6a47e-116">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="6a47e-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
