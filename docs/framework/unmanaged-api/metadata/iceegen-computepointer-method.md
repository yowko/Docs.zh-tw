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
ms.openlocfilehash: 41a3b9c77fc766b2fa39b406dedbb3203cc97ad9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715468"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="4193a-102">ICeeGen::ComputePointer 方法</span><span class="sxs-lookup"><span data-stu-id="4193a-102">ICeeGen::ComputePointer Method</span></span>

<span data-ttu-id="4193a-103">判斷指定程式碼區段的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="4193a-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="4193a-104">這個方法已經過時，不應該使用。</span><span class="sxs-lookup"><span data-stu-id="4193a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4193a-105">語法</span><span class="sxs-lookup"><span data-stu-id="4193a-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4193a-106">參數</span><span class="sxs-lookup"><span data-stu-id="4193a-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="4193a-107">在要傳回緩衝區的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="4193a-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="4193a-108">在取得指標之方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="4193a-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="4193a-109">擴展傳回之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="4193a-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4193a-110">需求</span><span class="sxs-lookup"><span data-stu-id="4193a-110">Requirements</span></span>  

 <span data-ttu-id="4193a-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4193a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4193a-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4193a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4193a-113">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4193a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4193a-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4193a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4193a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4193a-115">See also</span></span>

- [<span data-ttu-id="4193a-116">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="4193a-116">ICeeGen Interface</span></span>](iceegen-interface.md)
