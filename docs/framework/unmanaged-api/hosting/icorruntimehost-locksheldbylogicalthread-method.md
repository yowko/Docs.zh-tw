---
title: ICorRuntimeHost::LocksHeldByLogicalThread 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.LocksHeldByLogicalThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type:
- apiref
ms.openlocfilehash: 16f34d91861f9fcae51691ab13549bdf1ef333a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671495"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="eda29-102">ICorRuntimeHost::LocksHeldByLogicalThread 方法</span><span class="sxs-lookup"><span data-stu-id="eda29-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>

<span data-ttu-id="eda29-103">抓取目前線程保留的鎖定數目。</span><span class="sxs-lookup"><span data-stu-id="eda29-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="eda29-104">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="eda29-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eda29-105">語法</span><span class="sxs-lookup"><span data-stu-id="eda29-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eda29-106">參數</span><span class="sxs-lookup"><span data-stu-id="eda29-106">Parameters</span></span>  

 `pCount`  
 <span data-ttu-id="eda29-107">擴展目前線程所保存之鎖定數目的指標。</span><span class="sxs-lookup"><span data-stu-id="eda29-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eda29-108">需求</span><span class="sxs-lookup"><span data-stu-id="eda29-108">Requirements</span></span>  

 <span data-ttu-id="eda29-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eda29-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eda29-110">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="eda29-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eda29-111">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="eda29-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eda29-112">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="eda29-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda29-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eda29-113">See also</span></span>

- [<span data-ttu-id="eda29-114">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="eda29-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
