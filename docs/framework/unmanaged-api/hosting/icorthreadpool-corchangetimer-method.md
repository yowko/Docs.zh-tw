---
title: ICorThreadpool::CorChangeTimer 方法
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorChangeTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorChangeTimer
helpviewer_keywords:
- CorChangeTimer method [.NET Framework hosting]
- ICorThreadpool::CorChangeTimer method [.NET Framework hosting]
ms.assetid: 82b03a59-5a87-43ed-9b75-e04b256e1a46
topic_type:
- apiref
ms.openlocfilehash: 3d119c8355f5b58a05f1ea1695969b2e98682c72
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690222"
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="072a3-102">ICorThreadpool::CorChangeTimer 方法</span><span class="sxs-lookup"><span data-stu-id="072a3-102">ICorThreadpool::CorChangeTimer Method</span></span>

<span data-ttu-id="072a3-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="072a3-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="072a3-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="072a3-104">Syntax</span></span>  
  
```cpp  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,
    [in]  ULONG  DueTime,
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="072a3-105">需求</span><span class="sxs-lookup"><span data-stu-id="072a3-105">Requirements</span></span>  

 <span data-ttu-id="072a3-106">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="072a3-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="072a3-107">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="072a3-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="072a3-108">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="072a3-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="072a3-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="072a3-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="072a3-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="072a3-110">See also</span></span>

- [<span data-ttu-id="072a3-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="072a3-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
