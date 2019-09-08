---
title: GetIdentityAuthority 函式
ms.date: 03/30/2017
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f29246bdb929c8eaf1ebce726164d5cd2269b9f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796868"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="250d8-102">GetIdentityAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="250d8-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="250d8-103">取得[IIdentityAuthority](iidentityauthority-interface.md)實例的指標，它會管理程式碼物件的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="250d8-103">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="250d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="250d8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="250d8-105">參數</span><span class="sxs-lookup"><span data-stu-id="250d8-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="250d8-106">脫銷傳回`IIdentityAuthority`的指標。</span><span class="sxs-lookup"><span data-stu-id="250d8-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="250d8-107">需求</span><span class="sxs-lookup"><span data-stu-id="250d8-107">Requirements</span></span>  
 <span data-ttu-id="250d8-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="250d8-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="250d8-109">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="250d8-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="250d8-110">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="250d8-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="250d8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="250d8-111">See also</span></span>

- [<span data-ttu-id="250d8-112">IIdentityAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="250d8-112">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="250d8-113">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="250d8-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
