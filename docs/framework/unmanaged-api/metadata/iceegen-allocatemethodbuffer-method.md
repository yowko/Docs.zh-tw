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
ms.openlocfilehash: 38b9ea2ffab439f55f0a6d34d7f42c7669629168
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177916"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="1619f-102">ICeeGen::AllocateMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="1619f-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="1619f-103">為方法創建指定大小的緩衝區，並獲取方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="1619f-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="1619f-104">此方法已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="1619f-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1619f-105">語法</span><span class="sxs-lookup"><span data-stu-id="1619f-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1619f-106">參數</span><span class="sxs-lookup"><span data-stu-id="1619f-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="1619f-107">[在]要創建的緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="1619f-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="1619f-108">[出]返回的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1619f-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="1619f-109">[出]方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="1619f-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1619f-110">需求</span><span class="sxs-lookup"><span data-stu-id="1619f-110">Requirements</span></span>  
 <span data-ttu-id="1619f-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1619f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1619f-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="1619f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1619f-113">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1619f-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1619f-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1619f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1619f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1619f-115">See also</span></span>

- [<span data-ttu-id="1619f-116">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="1619f-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
