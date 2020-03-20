---
title: ICeeGen::ComputePointer 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 9587bbe8f087fd9a51bba67492af1d5acb53ae4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176093"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="f3848-102">ICeeGen::ComputePointer 方法</span><span class="sxs-lookup"><span data-stu-id="f3848-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="f3848-103">確定指定代碼部分的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f3848-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="f3848-104">此方法已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="f3848-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3848-105">語法</span><span class="sxs-lookup"><span data-stu-id="f3848-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3848-106">參數</span><span class="sxs-lookup"><span data-stu-id="f3848-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="f3848-107">[在]要為其返回緩衝區的代碼部分。</span><span class="sxs-lookup"><span data-stu-id="f3848-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="f3848-108">[在]要為其獲取指標的方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="f3848-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="f3848-109">[出]指向返回的緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="f3848-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3848-110">需求</span><span class="sxs-lookup"><span data-stu-id="f3848-110">Requirements</span></span>  
 <span data-ttu-id="f3848-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3848-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3848-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="f3848-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3848-113">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f3848-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3848-114">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3848-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3848-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3848-115">See also</span></span>

- [<span data-ttu-id="f3848-116">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="f3848-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
