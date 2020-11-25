---
title: IAssemblyEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.Clone
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::Clone
helpviewer_keywords:
- Clone method, IAssemblyEnum interface [.NET Framework fusion]
- IAssemblyEnum::Clone method [.NET Framework fusion]
ms.assetid: 0014bb66-590c-486c-9ade-f2133905cd99
topic_type:
- apiref
ms.openlocfilehash: e1eef43858e4f38888f9f31e3076b092fbdd5633
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719901"
---
# <a name="iassemblyenumclone-method"></a><span data-ttu-id="b1a27-102">IAssemblyEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="b1a27-102">IAssemblyEnum::Clone Method</span></span>

<span data-ttu-id="b1a27-103">建立這個 [IAssemblyEnum](iassemblyenum-interface.md) 物件的淺層複本。</span><span class="sxs-lookup"><span data-stu-id="b1a27-103">Creates a shallow copy of this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a27-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1a27-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1a27-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1a27-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="b1a27-106">擴展複製的指標。</span><span class="sxs-lookup"><span data-stu-id="b1a27-106">[out] A pointer to the copy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1a27-107">需求</span><span class="sxs-lookup"><span data-stu-id="b1a27-107">Requirements</span></span>  

 <span data-ttu-id="b1a27-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1a27-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1a27-109">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="b1a27-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b1a27-110">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1a27-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a27-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1a27-111">See also</span></span>

- [<span data-ttu-id="b1a27-112">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="b1a27-112">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
