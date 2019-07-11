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
ms.openlocfilehash: 96968de84182b74f7baa89d5dfc12a4797ade595
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779224"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="48965-102">CreateICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="48965-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="48965-103">會建立[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="48965-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="48965-104">此函式已被取代，在.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="48965-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48965-105">語法</span><span class="sxs-lookup"><span data-stu-id="48965-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48965-106">參數</span><span class="sxs-lookup"><span data-stu-id="48965-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="48965-107">[out]新的位址指標`ICeeFileGen`物件。</span><span class="sxs-lookup"><span data-stu-id="48965-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48965-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="48965-108">Return Value</span></span>  
 <span data-ttu-id="48965-109">這個方法會傳回標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="48965-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48965-110">備註</span><span class="sxs-lookup"><span data-stu-id="48965-110">Remarks</span></span>  
 <span data-ttu-id="48965-111">`ICeeFileGen`物件用來建立通用語言執行平台 (CLR) 可移植執行檔 (PE) 檔案。</span><span class="sxs-lookup"><span data-stu-id="48965-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="48965-112">呼叫[DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)函式終結`ICeeFileGen`物件時完成。</span><span class="sxs-lookup"><span data-stu-id="48965-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48965-113">需求</span><span class="sxs-lookup"><span data-stu-id="48965-113">Requirements</span></span>  
 <span data-ttu-id="48965-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="48965-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48965-115">**標頭：** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="48965-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="48965-116">**LIBRARY:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="48965-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="48965-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48965-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48965-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48965-118">See also</span></span>

- [<span data-ttu-id="48965-119">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="48965-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
