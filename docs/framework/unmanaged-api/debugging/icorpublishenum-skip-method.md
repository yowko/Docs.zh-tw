---
title: ICorPublishEnum::Skip 方法
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type:
- apiref
ms.openlocfilehash: 888cc40c194cb86b0f898f5556ea14b8897e08c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693303"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="ad155-102">ICorPublishEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="ad155-102">ICorPublishEnum::Skip Method</span></span>

<span data-ttu-id="ad155-103">依指定的專案數將游標向前移動至列舉。</span><span class="sxs-lookup"><span data-stu-id="ad155-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad155-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad155-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad155-105">參數</span><span class="sxs-lookup"><span data-stu-id="ad155-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="ad155-106">在要向前移動游標的專案數目。</span><span class="sxs-lookup"><span data-stu-id="ad155-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad155-107">需求</span><span class="sxs-lookup"><span data-stu-id="ad155-107">Requirements</span></span>  

 <span data-ttu-id="ad155-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad155-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad155-109">**標頭：** CorPub .idl、CorPub。h</span><span class="sxs-lookup"><span data-stu-id="ad155-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ad155-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad155-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad155-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad155-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad155-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad155-112">See also</span></span>

- [<span data-ttu-id="ad155-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="ad155-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
