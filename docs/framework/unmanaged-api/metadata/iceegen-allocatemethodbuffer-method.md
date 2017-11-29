---
title: "ICeeGen::AllocateMethodBuffer 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.AllocateMethodBuffer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be288bedf12649b4356c68135868b9415840c4d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="b047e-102">ICeeGen::AllocateMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="b047e-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="b047e-103">建立方法，指定大小的緩衝區，並取得方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="b047e-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="b047e-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="b047e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b047e-105">語法</span><span class="sxs-lookup"><span data-stu-id="b047e-105">Syntax</span></span>  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b047e-106">參數</span><span class="sxs-lookup"><span data-stu-id="b047e-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="b047e-107">[in]要建立之緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="b047e-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="b047e-108">[out]傳回的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b047e-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="b047e-109">[out]方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="b047e-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b047e-110">需求</span><span class="sxs-lookup"><span data-stu-id="b047e-110">Requirements</span></span>  
 <span data-ttu-id="b047e-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b047e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b047e-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b047e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b047e-113">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b047e-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b047e-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b047e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b047e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b047e-115">See Also</span></span>  
 [<span data-ttu-id="b047e-116">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="b047e-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
