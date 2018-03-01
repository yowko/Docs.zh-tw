---
title: "DestroyICeeFileGen 函式"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d6c3e326aa71adc1bc9abe350cfc0528c88905cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="e6676-102">DestroyICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="e6676-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="e6676-103">終結[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="e6676-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="e6676-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e6676-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6676-105">語法</span><span class="sxs-lookup"><span data-stu-id="e6676-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6676-106">參數</span><span class="sxs-lookup"><span data-stu-id="e6676-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="e6676-107">[in]`ICeeFileGen`終結物件。</span><span class="sxs-lookup"><span data-stu-id="e6676-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6676-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e6676-108">Return Value</span></span>  
 <span data-ttu-id="e6676-109">這個方法會傳回標準的 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e6676-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6676-110">備註</span><span class="sxs-lookup"><span data-stu-id="e6676-110">Remarks</span></span>  
 <span data-ttu-id="e6676-111">`DestroyICeeFileGen`終結`ICeeFileGen`所建立的物件[CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="e6676-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6676-112">需求</span><span class="sxs-lookup"><span data-stu-id="e6676-112">Requirements</span></span>  
 <span data-ttu-id="e6676-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6676-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6676-114">**標頭：** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="e6676-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="e6676-115">**程式庫：** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="e6676-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="e6676-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6676-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6676-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="e6676-117">See Also</span></span>  
 [<span data-ttu-id="e6676-118">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="e6676-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
