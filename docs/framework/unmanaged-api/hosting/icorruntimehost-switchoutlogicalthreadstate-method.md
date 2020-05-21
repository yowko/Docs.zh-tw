---
title: ICorRuntimeHost::SwitchOutLogicalThreadState 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchOutLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type:
- apiref
ms.openlocfilehash: f32381dc40a744157e46780e59b83efd63e58dcb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762639"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="b2f39-102">ICorRuntimeHost::SwitchOutLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="b2f39-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="b2f39-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="b2f39-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2f39-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2f39-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2f39-105">參數</span><span class="sxs-lookup"><span data-stu-id="b2f39-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="b2f39-106">脫銷Cookie，表示正在切換的光纖。</span><span class="sxs-lookup"><span data-stu-id="b2f39-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2f39-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="b2f39-107">Requirements</span></span>  
 <span data-ttu-id="b2f39-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2f39-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2f39-109">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b2f39-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2f39-110">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b2f39-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2f39-111">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="b2f39-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2f39-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2f39-112">See also</span></span>

- [<span data-ttu-id="b2f39-113">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="b2f39-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
