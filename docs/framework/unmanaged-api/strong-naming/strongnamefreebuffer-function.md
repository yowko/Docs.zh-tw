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
ms.openlocfilehash: 1a129608370cd72967e0c441eff12b4aca7e638c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455084"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="db023-102">StrongNameFreeBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="db023-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="db023-103">釋放記憶體配置與先前的強式名稱的函式呼叫這類[StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)， [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)，或[StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="db023-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="db023-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="db023-104">This function has been deprecated.</span></span> <span data-ttu-id="db023-105">使用[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="db023-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db023-106">語法</span><span class="sxs-lookup"><span data-stu-id="db023-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db023-107">參數</span><span class="sxs-lookup"><span data-stu-id="db023-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="db023-108">[in]要釋放的記憶體指標。</span><span class="sxs-lookup"><span data-stu-id="db023-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db023-109">需求</span><span class="sxs-lookup"><span data-stu-id="db023-109">Requirements</span></span>  
 <span data-ttu-id="db023-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db023-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db023-111">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="db023-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="db023-112">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="db023-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db023-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db023-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db023-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db023-114">See Also</span></span>  
 [<span data-ttu-id="db023-115">StrongNameFreeBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="db023-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
 [<span data-ttu-id="db023-116">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="db023-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
