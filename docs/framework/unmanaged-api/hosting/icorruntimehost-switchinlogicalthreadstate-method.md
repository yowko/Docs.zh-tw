---
title: ICorRuntimeHost::SwitchInLogicalThreadState 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
ms.openlocfilehash: a4590bcd96226a713ff5535a8bc802c2116f862a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690131"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="a6dae-102">ICorRuntimeHost::SwitchInLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="a6dae-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>

<span data-ttu-id="a6dae-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="a6dae-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6dae-104">語法</span><span class="sxs-lookup"><span data-stu-id="a6dae-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6dae-105">參數</span><span class="sxs-lookup"><span data-stu-id="a6dae-105">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="a6dae-106">在表示要使用之光纖的 Cookie。</span><span class="sxs-lookup"><span data-stu-id="a6dae-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6dae-107">需求</span><span class="sxs-lookup"><span data-stu-id="a6dae-107">Requirements</span></span>  

 <span data-ttu-id="a6dae-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6dae-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6dae-109">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a6dae-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6dae-110">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="a6dae-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6dae-111">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="a6dae-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6dae-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6dae-112">See also</span></span>

- [<span data-ttu-id="a6dae-113">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="a6dae-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
