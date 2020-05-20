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
ms.openlocfilehash: 7ed4236187fab1c1e81be9ddcdff1f1852e38f70
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421185"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="548fe-102">ICorPublishEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="548fe-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="548fe-103">取得列舉中的專案數。</span><span class="sxs-lookup"><span data-stu-id="548fe-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="548fe-104">語法</span><span class="sxs-lookup"><span data-stu-id="548fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="548fe-105">參數</span><span class="sxs-lookup"><span data-stu-id="548fe-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="548fe-106">脫銷列舉中專案數的指標。</span><span class="sxs-lookup"><span data-stu-id="548fe-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="548fe-107">需求</span><span class="sxs-lookup"><span data-stu-id="548fe-107">Requirements</span></span>  
 <span data-ttu-id="548fe-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="548fe-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="548fe-109">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="548fe-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="548fe-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="548fe-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="548fe-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="548fe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="548fe-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="548fe-112">See also</span></span>

- [<span data-ttu-id="548fe-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="548fe-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
