---
title: "ICeeGen::ComputePointer 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0b027615f7697b9ea103d44bea0ec44834fe3f04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="c617c-102">ICeeGen::ComputePointer 方法</span><span class="sxs-lookup"><span data-stu-id="c617c-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="c617c-103">判斷指定的程式碼區段的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c617c-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="c617c-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="c617c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c617c-105">語法</span><span class="sxs-lookup"><span data-stu-id="c617c-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c617c-106">參數</span><span class="sxs-lookup"><span data-stu-id="c617c-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="c617c-107">[in]要傳回緩衝區的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="c617c-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="c617c-108">[in]要取得的指標方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="c617c-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="c617c-109">[out]傳回緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="c617c-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c617c-110">需求</span><span class="sxs-lookup"><span data-stu-id="c617c-110">Requirements</span></span>  
 <span data-ttu-id="c617c-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c617c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c617c-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c617c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c617c-113">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c617c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c617c-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c617c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c617c-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="c617c-115">See Also</span></span>  
 [<span data-ttu-id="c617c-116">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="c617c-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
