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
ms.openlocfilehash: bd51f9c05c49fefc790ce69dcdc3117680c8e6b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500025"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="33538-102">ICeeGen::AllocateMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="33538-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="33538-103">建立方法中，指定大小的緩衝區，並取得方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="33538-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="33538-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="33538-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33538-105">語法</span><span class="sxs-lookup"><span data-stu-id="33538-105">Syntax</span></span>  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33538-106">參數</span><span class="sxs-lookup"><span data-stu-id="33538-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="33538-107">[in]要建立之緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="33538-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="33538-108">[out]傳回的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="33538-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="33538-109">[out]方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="33538-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33538-110">需求</span><span class="sxs-lookup"><span data-stu-id="33538-110">Requirements</span></span>  
 <span data-ttu-id="33538-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33538-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33538-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="33538-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33538-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="33538-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="33538-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33538-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33538-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33538-115">See also</span></span>
- [<span data-ttu-id="33538-116">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="33538-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
