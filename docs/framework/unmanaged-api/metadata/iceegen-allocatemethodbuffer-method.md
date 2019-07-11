---
title: ICeeGen::AllocateMethodBuffer 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 080c16d3a7baceaa277b3418ac2e17391090f00c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750603"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="afe3b-102">ICeeGen::AllocateMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="afe3b-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="afe3b-103">建立方法中，指定大小的緩衝區，並取得方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="afe3b-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="afe3b-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="afe3b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afe3b-105">語法</span><span class="sxs-lookup"><span data-stu-id="afe3b-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afe3b-106">參數</span><span class="sxs-lookup"><span data-stu-id="afe3b-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="afe3b-107">[in]要建立之緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="afe3b-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="afe3b-108">[out]傳回的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="afe3b-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="afe3b-109">[out]方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="afe3b-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afe3b-110">需求</span><span class="sxs-lookup"><span data-stu-id="afe3b-110">Requirements</span></span>  
 <span data-ttu-id="afe3b-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="afe3b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afe3b-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="afe3b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="afe3b-113">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="afe3b-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="afe3b-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afe3b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe3b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afe3b-115">See also</span></span>

- [<span data-ttu-id="afe3b-116">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="afe3b-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
