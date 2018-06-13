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
ms.openlocfilehash: f56376d4400f4e24aefe2d1e5d4ad504b1d281cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446000"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="d158f-102">ICeeGen::AllocateMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="d158f-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="d158f-103">建立方法，指定大小的緩衝區，並取得方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="d158f-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="d158f-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="d158f-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d158f-105">語法</span><span class="sxs-lookup"><span data-stu-id="d158f-105">Syntax</span></span>  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d158f-106">參數</span><span class="sxs-lookup"><span data-stu-id="d158f-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="d158f-107">[in]要建立之緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="d158f-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="d158f-108">[out]傳回的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d158f-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="d158f-109">[out]方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="d158f-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d158f-110">需求</span><span class="sxs-lookup"><span data-stu-id="d158f-110">Requirements</span></span>  
 <span data-ttu-id="d158f-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d158f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d158f-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d158f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d158f-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d158f-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d158f-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d158f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d158f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d158f-115">See Also</span></span>  
 [<span data-ttu-id="d158f-116">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="d158f-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
