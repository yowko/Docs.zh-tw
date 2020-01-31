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
ms.openlocfilehash: bd62fb38352022f69c45d2a5921973cfbec1c6e4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790596"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="a9a91-102">ICorPublishEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="a9a91-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="a9a91-103">在列舉中，將資料指標向後移動指定的專案數。</span><span class="sxs-lookup"><span data-stu-id="a9a91-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9a91-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9a91-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9a91-105">參數</span><span class="sxs-lookup"><span data-stu-id="a9a91-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a9a91-106">在要將資料指標向前移動的專案數。</span><span class="sxs-lookup"><span data-stu-id="a9a91-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9a91-107">需求</span><span class="sxs-lookup"><span data-stu-id="a9a91-107">Requirements</span></span>  
 <span data-ttu-id="a9a91-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9a91-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9a91-109">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="a9a91-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a9a91-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9a91-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9a91-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9a91-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a91-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="a9a91-112">See also</span></span>

- [<span data-ttu-id="a9a91-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a9a91-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
