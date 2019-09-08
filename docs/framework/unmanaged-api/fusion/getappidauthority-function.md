---
title: GetAppIdAuthority 函式
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8471610008bee02c7cc4e7654b21d6aca5dcf53a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796281"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="04d5b-102">GetAppIdAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="04d5b-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="04d5b-103">取得[IAppIdAuthority](iappidauthority-interface.md)實例的指標，它會管理應用程式識別和參考的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="04d5b-103">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04d5b-104">語法</span><span class="sxs-lookup"><span data-stu-id="04d5b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="04d5b-105">參數</span><span class="sxs-lookup"><span data-stu-id="04d5b-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="04d5b-106">脫銷傳回`IAppIdAuthority`的指標。</span><span class="sxs-lookup"><span data-stu-id="04d5b-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04d5b-107">需求</span><span class="sxs-lookup"><span data-stu-id="04d5b-107">Requirements</span></span>  
 <span data-ttu-id="04d5b-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04d5b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04d5b-109">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="04d5b-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="04d5b-110">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04d5b-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d5b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04d5b-111">See also</span></span>

- [<span data-ttu-id="04d5b-112">IAppIdAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="04d5b-112">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)
- [<span data-ttu-id="04d5b-113">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="04d5b-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
