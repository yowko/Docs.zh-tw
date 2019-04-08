---
title: CreateICeeFileGen 函式
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 566f73335861a8eb769b21a254e0e93b51a78d02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151810"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="0eb29-102">CreateICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="0eb29-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="0eb29-103">會建立[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="0eb29-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="0eb29-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0eb29-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eb29-105">語法</span><span class="sxs-lookup"><span data-stu-id="0eb29-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0eb29-106">參數</span><span class="sxs-lookup"><span data-stu-id="0eb29-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="0eb29-107">[out]新的位址指標`ICeeFileGen`物件。</span><span class="sxs-lookup"><span data-stu-id="0eb29-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0eb29-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="0eb29-108">Return Value</span></span>  
 <span data-ttu-id="0eb29-109">這個方法會傳回標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="0eb29-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0eb29-110">備註</span><span class="sxs-lookup"><span data-stu-id="0eb29-110">Remarks</span></span>  
 <span data-ttu-id="0eb29-111">`ICeeFileGen`物件用來建立通用語言執行平台 (CLR) 可移植執行檔 (PE) 檔案。</span><span class="sxs-lookup"><span data-stu-id="0eb29-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="0eb29-112">呼叫[DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)函式終結`ICeeFileGen`物件時完成。</span><span class="sxs-lookup"><span data-stu-id="0eb29-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eb29-113">需求</span><span class="sxs-lookup"><span data-stu-id="0eb29-113">Requirements</span></span>  
 <span data-ttu-id="0eb29-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0eb29-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eb29-115">**標頭：** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="0eb29-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="0eb29-116">**LIBRARY:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="0eb29-116">**Library:** MSCorPE.dll</span></span>  
  
 **<span data-ttu-id="0eb29-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="0eb29-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0eb29-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0eb29-118">See also</span></span>

- [<span data-ttu-id="0eb29-119">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="0eb29-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
