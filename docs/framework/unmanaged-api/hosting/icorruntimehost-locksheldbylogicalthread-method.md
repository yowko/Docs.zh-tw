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
ms.openlocfilehash: 265ab5ae03b7b42c4f5f429df5d659d60e55f18e
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760715"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="9ff53-102">ICorRuntimeHost::LocksHeldByLogicalThread 方法</span><span class="sxs-lookup"><span data-stu-id="9ff53-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="9ff53-103">抓取目前線程持有的鎖定數目。</span><span class="sxs-lookup"><span data-stu-id="9ff53-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="9ff53-104">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="9ff53-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ff53-105">語法</span><span class="sxs-lookup"><span data-stu-id="9ff53-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ff53-106">參數</span><span class="sxs-lookup"><span data-stu-id="9ff53-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="9ff53-107">脫銷目前線程所持有的鎖定數目指標。</span><span class="sxs-lookup"><span data-stu-id="9ff53-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ff53-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="9ff53-108">Requirements</span></span>  
 <span data-ttu-id="9ff53-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ff53-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ff53-110">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="9ff53-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ff53-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9ff53-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ff53-112">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="9ff53-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff53-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ff53-113">See also</span></span>

- [<span data-ttu-id="9ff53-114">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="9ff53-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
