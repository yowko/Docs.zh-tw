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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044963"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="f40cb-102">ICeeGen::GetMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="f40cb-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="f40cb-103">取得方法的適當大小的緩衝區，在指定的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="f40cb-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="f40cb-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="f40cb-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f40cb-105">語法</span><span class="sxs-lookup"><span data-stu-id="f40cb-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f40cb-106">參數</span><span class="sxs-lookup"><span data-stu-id="f40cb-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="f40cb-107">[in]要傳回緩衝區方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="f40cb-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="f40cb-108">[out]傳回緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="f40cb-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f40cb-109">需求</span><span class="sxs-lookup"><span data-stu-id="f40cb-109">Requirements</span></span>  
 <span data-ttu-id="f40cb-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f40cb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f40cb-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f40cb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f40cb-112">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f40cb-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f40cb-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f40cb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f40cb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f40cb-114">See also</span></span>

- [<span data-ttu-id="f40cb-115">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="f40cb-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
