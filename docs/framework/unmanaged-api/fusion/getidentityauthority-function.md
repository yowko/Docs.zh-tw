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
ms.openlocfilehash: e9631211993afbfe968c7122828251746f15c3f6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732121"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="f2a64-102">GetIdentityAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="f2a64-102">GetIdentityAuthority Function</span></span>

<span data-ttu-id="f2a64-103">取得 [IIdentityAuthority](iidentityauthority-interface.md) 實例的指標，該實例會管理程式碼物件的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2a64-103">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a64-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2a64-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2a64-105">參數</span><span class="sxs-lookup"><span data-stu-id="f2a64-105">Parameters</span></span>  

 `ppIIdentityAuthority`  
 <span data-ttu-id="f2a64-106">擴展傳回的 `IIdentityAuthority` 指標。</span><span class="sxs-lookup"><span data-stu-id="f2a64-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2a64-107">需求</span><span class="sxs-lookup"><span data-stu-id="f2a64-107">Requirements</span></span>  

 <span data-ttu-id="f2a64-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2a64-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2a64-109">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="f2a64-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="f2a64-110">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2a64-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a64-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2a64-111">See also</span></span>

- [<span data-ttu-id="f2a64-112">IIdentityAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="f2a64-112">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="f2a64-113">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="f2a64-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
