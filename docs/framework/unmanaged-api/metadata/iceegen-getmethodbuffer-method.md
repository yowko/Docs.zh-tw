---
title: ICeeGen::GetMethodBuffer 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0aea6185095a30aae9197c875aa9b9ac581d406
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121533"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="e3c54-102">ICeeGen::GetMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="e3c54-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="e3c54-103">取得方法的適當大小的緩衝區，在指定的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="e3c54-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="e3c54-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="e3c54-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3c54-105">語法</span><span class="sxs-lookup"><span data-stu-id="e3c54-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3c54-106">參數</span><span class="sxs-lookup"><span data-stu-id="e3c54-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="e3c54-107">[in]要傳回緩衝區方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="e3c54-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="e3c54-108">[out]傳回緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="e3c54-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3c54-109">需求</span><span class="sxs-lookup"><span data-stu-id="e3c54-109">Requirements</span></span>  
 <span data-ttu-id="e3c54-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e3c54-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3c54-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e3c54-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3c54-112">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e3c54-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="e3c54-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="e3c54-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e3c54-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3c54-114">See also</span></span>

- [<span data-ttu-id="e3c54-115">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="e3c54-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
