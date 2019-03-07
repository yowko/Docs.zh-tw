---
title: DestroyICeeFileGen 函式
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50bfe38bc4c4843ac0954a6c816e5dc06b5e0fed
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501951"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="0f74b-102">DestroyICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="0f74b-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="0f74b-103">終結[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="0f74b-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="0f74b-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0f74b-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f74b-105">語法</span><span class="sxs-lookup"><span data-stu-id="0f74b-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f74b-106">參數</span><span class="sxs-lookup"><span data-stu-id="0f74b-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="0f74b-107">[in]`ICeeFileGen`終結的物件。</span><span class="sxs-lookup"><span data-stu-id="0f74b-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f74b-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="0f74b-108">Return Value</span></span>  
 <span data-ttu-id="0f74b-109">這個方法會傳回標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="0f74b-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f74b-110">備註</span><span class="sxs-lookup"><span data-stu-id="0f74b-110">Remarks</span></span>  
 <span data-ttu-id="0f74b-111">`DestroyICeeFileGen` 終結`ICeeFileGen`所建立的物件[CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="0f74b-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f74b-112">需求</span><span class="sxs-lookup"><span data-stu-id="0f74b-112">Requirements</span></span>  
 <span data-ttu-id="0f74b-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0f74b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f74b-114">**標頭：** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="0f74b-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="0f74b-115">**程式庫：** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="0f74b-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="0f74b-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f74b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f74b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f74b-117">See also</span></span>
- [<span data-ttu-id="0f74b-118">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="0f74b-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
