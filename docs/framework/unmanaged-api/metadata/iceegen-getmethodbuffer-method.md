---
title: "ICeeGen::GetMethodBuffer 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetMethodBuffer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23beea4bd991b21b30375c9297efb945c3dbab75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="6fb39-102">ICeeGen::GetMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="6fb39-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="6fb39-103">在指定的相對虛擬位址的方法取得適當大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6fb39-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="6fb39-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="6fb39-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fb39-105">語法</span><span class="sxs-lookup"><span data-stu-id="6fb39-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6fb39-106">參數</span><span class="sxs-lookup"><span data-stu-id="6fb39-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="6fb39-107">[in]要傳回緩衝區方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="6fb39-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="6fb39-108">[out]傳回緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="6fb39-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fb39-109">需求</span><span class="sxs-lookup"><span data-stu-id="6fb39-109">Requirements</span></span>  
 <span data-ttu-id="6fb39-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6fb39-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fb39-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6fb39-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6fb39-112">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6fb39-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6fb39-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fb39-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb39-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="6fb39-114">See Also</span></span>  
 [<span data-ttu-id="6fb39-115">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="6fb39-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
