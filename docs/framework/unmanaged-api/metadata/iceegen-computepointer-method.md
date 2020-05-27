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
ms.openlocfilehash: 206dcd3a0a82da9b6211c8c2045e4e9d3d991973
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008868"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="ee76e-102">ICeeGen::ComputePointer 方法</span><span class="sxs-lookup"><span data-stu-id="ee76e-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="ee76e-103">判斷指定之程式碼區段的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ee76e-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="ee76e-104">這個方法已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="ee76e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee76e-105">語法</span><span class="sxs-lookup"><span data-stu-id="ee76e-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee76e-106">參數</span><span class="sxs-lookup"><span data-stu-id="ee76e-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="ee76e-107">在要傳回緩衝區的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="ee76e-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="ee76e-108">在要取得指標之方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="ee76e-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="ee76e-109">脫銷傳回之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="ee76e-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee76e-110">需求</span><span class="sxs-lookup"><span data-stu-id="ee76e-110">Requirements</span></span>  
 <span data-ttu-id="ee76e-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee76e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee76e-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ee76e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee76e-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ee76e-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ee76e-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee76e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee76e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee76e-115">See also</span></span>

- [<span data-ttu-id="ee76e-116">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="ee76e-116">ICeeGen Interface</span></span>](iceegen-interface.md)
