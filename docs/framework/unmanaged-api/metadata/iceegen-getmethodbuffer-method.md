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
ms.openlocfilehash: e9c2dab9f30be6e5eea8f6570b297f8df11b6fe6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715325"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="ecd93-102">ICeeGen::GetMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="ecd93-102">ICeeGen::GetMethodBuffer Method</span></span>

<span data-ttu-id="ecd93-103">取得指定的相對虛擬位址之方法適當大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ecd93-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="ecd93-104">這個方法已經過時，不應該使用。</span><span class="sxs-lookup"><span data-stu-id="ecd93-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecd93-105">語法</span><span class="sxs-lookup"><span data-stu-id="ecd93-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecd93-106">參數</span><span class="sxs-lookup"><span data-stu-id="ecd93-106">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="ecd93-107">在傳回緩衝區之方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="ecd93-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="ecd93-108">擴展傳回之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="ecd93-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecd93-109">需求</span><span class="sxs-lookup"><span data-stu-id="ecd93-109">Requirements</span></span>  

 <span data-ttu-id="ecd93-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ecd93-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecd93-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ecd93-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ecd93-112">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ecd93-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ecd93-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecd93-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecd93-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecd93-114">See also</span></span>

- [<span data-ttu-id="ecd93-115">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="ecd93-115">ICeeGen Interface</span></span>](iceegen-interface.md)
