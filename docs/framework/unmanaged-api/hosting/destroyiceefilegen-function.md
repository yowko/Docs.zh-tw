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
ms.openlocfilehash: ab4560774edce49341c86dd9446e38701db7fa62
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769828"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="4c0a2-102">DestroyICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="4c0a2-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="4c0a2-103">終結[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="4c0a2-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="4c0a2-104">此函式已被取代，在.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="4c0a2-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c0a2-105">語法</span><span class="sxs-lookup"><span data-stu-id="4c0a2-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c0a2-106">參數</span><span class="sxs-lookup"><span data-stu-id="4c0a2-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="4c0a2-107">[in]`ICeeFileGen`終結的物件。</span><span class="sxs-lookup"><span data-stu-id="4c0a2-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c0a2-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="4c0a2-108">Return Value</span></span>  
 <span data-ttu-id="4c0a2-109">這個方法會傳回標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4c0a2-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c0a2-110">備註</span><span class="sxs-lookup"><span data-stu-id="4c0a2-110">Remarks</span></span>  
 <span data-ttu-id="4c0a2-111">`DestroyICeeFileGen` 終結`ICeeFileGen`所建立的物件[CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="4c0a2-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c0a2-112">需求</span><span class="sxs-lookup"><span data-stu-id="4c0a2-112">Requirements</span></span>  
 <span data-ttu-id="4c0a2-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c0a2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c0a2-114">**標頭：** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="4c0a2-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="4c0a2-115">**LIBRARY:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="4c0a2-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="4c0a2-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c0a2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c0a2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c0a2-117">See also</span></span>

- [<span data-ttu-id="4c0a2-118">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="4c0a2-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
