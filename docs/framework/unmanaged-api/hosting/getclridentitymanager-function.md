---
title: GetCLRIdentityManager 函式
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
ms.openlocfilehash: 57f771d933e896677dfc0bd5d9dac58da2af22c8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617252"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="17e9d-102">GetCLRIdentityManager 函式</span><span class="sxs-lookup"><span data-stu-id="17e9d-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="17e9d-103">取得介面的指標，允許 common language runtime （CLR）管理身分識別。</span><span class="sxs-lookup"><span data-stu-id="17e9d-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="17e9d-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="17e9d-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17e9d-105">語法</span><span class="sxs-lookup"><span data-stu-id="17e9d-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17e9d-106">參數</span><span class="sxs-lookup"><span data-stu-id="17e9d-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="17e9d-107">在`REFIID`指定要取得之介面的（介面識別碼）。</span><span class="sxs-lookup"><span data-stu-id="17e9d-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="17e9d-108">這個值必須是 IID_ICLRAssemblyIdentityManager 或 IID_ICLRHostBindingPolicyManager。</span><span class="sxs-lookup"><span data-stu-id="17e9d-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="17e9d-109">脫銷[ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)或[ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md)物件之位址的指標。</span><span class="sxs-lookup"><span data-stu-id="17e9d-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17e9d-110">備註</span><span class="sxs-lookup"><span data-stu-id="17e9d-110">Remarks</span></span>  
 <span data-ttu-id="17e9d-111">呼叫[GetRealProcAddress](getrealprocaddress-function.md)函式以取得函式的指標 `GetCLRIdentityManager` 。</span><span class="sxs-lookup"><span data-stu-id="17e9d-111">Call the [GetRealProcAddress](getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17e9d-112">需求</span><span class="sxs-lookup"><span data-stu-id="17e9d-112">Requirements</span></span>  
 <span data-ttu-id="17e9d-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17e9d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17e9d-114">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="17e9d-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17e9d-115">連結**庫：** Mscorwks.dll .dll</span><span class="sxs-lookup"><span data-stu-id="17e9d-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="17e9d-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17e9d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e9d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17e9d-117">See also</span></span>

- [<span data-ttu-id="17e9d-118">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="17e9d-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
