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
ms.openlocfilehash: eb9e5bdf85c6d487fd82422522854076c03e2288
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140459"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="73749-102">ICorPublishEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="73749-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="73749-103">在列舉中，將資料指標向後移動指定的專案數。</span><span class="sxs-lookup"><span data-stu-id="73749-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73749-104">語法</span><span class="sxs-lookup"><span data-stu-id="73749-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73749-105">參數</span><span class="sxs-lookup"><span data-stu-id="73749-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="73749-106">在要將資料指標向前移動的專案數。</span><span class="sxs-lookup"><span data-stu-id="73749-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73749-107">需求</span><span class="sxs-lookup"><span data-stu-id="73749-107">Requirements</span></span>  
 <span data-ttu-id="73749-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73749-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73749-109">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="73749-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="73749-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73749-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73749-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73749-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73749-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="73749-112">See also</span></span>

- [<span data-ttu-id="73749-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="73749-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
