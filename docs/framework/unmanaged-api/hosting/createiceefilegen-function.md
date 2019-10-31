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
ms.openlocfilehash: de27851b4afc3eccad46531848c68723bff346d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136828"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="b7fdd-102">CreateICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="b7fdd-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="b7fdd-103">建立[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="b7fdd-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="b7fdd-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="b7fdd-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7fdd-105">語法</span><span class="sxs-lookup"><span data-stu-id="b7fdd-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7fdd-106">參數</span><span class="sxs-lookup"><span data-stu-id="b7fdd-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="b7fdd-107">脫銷新 `ICeeFileGen` 物件之位址的指標。</span><span class="sxs-lookup"><span data-stu-id="b7fdd-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7fdd-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b7fdd-108">Return Value</span></span>  
 <span data-ttu-id="b7fdd-109">這個方法會傳回標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="b7fdd-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7fdd-110">備註</span><span class="sxs-lookup"><span data-stu-id="b7fdd-110">Remarks</span></span>  
 <span data-ttu-id="b7fdd-111">`ICeeFileGen` 物件是用來建立 common language runtime （CLR）可移植執行檔（PE）檔案。</span><span class="sxs-lookup"><span data-stu-id="b7fdd-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="b7fdd-112">完成時，呼叫[DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)函式以終結 `ICeeFileGen` 物件。</span><span class="sxs-lookup"><span data-stu-id="b7fdd-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7fdd-113">需求</span><span class="sxs-lookup"><span data-stu-id="b7fdd-113">Requirements</span></span>  
 <span data-ttu-id="b7fdd-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7fdd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7fdd-115">**標頭：** ICeeFileGen。h</span><span class="sxs-lookup"><span data-stu-id="b7fdd-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="b7fdd-116">連結**庫：** MSCorPE .dll</span><span class="sxs-lookup"><span data-stu-id="b7fdd-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="b7fdd-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7fdd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7fdd-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7fdd-118">See also</span></span>

- [<span data-ttu-id="b7fdd-119">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="b7fdd-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
