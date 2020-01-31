---
title: ICorPublishEnum::GetCount 方法
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type:
- apiref
ms.openlocfilehash: 0b3754fbcca50b52039dc358aed7070b8a152ead
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790628"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="c99f6-102">ICorPublishEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="c99f6-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="c99f6-103">取得列舉中的專案數。</span><span class="sxs-lookup"><span data-stu-id="c99f6-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c99f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="c99f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c99f6-105">參數</span><span class="sxs-lookup"><span data-stu-id="c99f6-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="c99f6-106">脫銷列舉中專案數的指標。</span><span class="sxs-lookup"><span data-stu-id="c99f6-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c99f6-107">需求</span><span class="sxs-lookup"><span data-stu-id="c99f6-107">Requirements</span></span>  
 <span data-ttu-id="c99f6-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c99f6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c99f6-109">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="c99f6-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c99f6-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c99f6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c99f6-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c99f6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c99f6-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="c99f6-112">See also</span></span>

- [<span data-ttu-id="c99f6-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="c99f6-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
