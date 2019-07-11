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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ea4947582e4e8bfdb6873a90c5284e9ae9d8a62
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736248"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="a3dee-102">GetCLRIdentityManager 函式</span><span class="sxs-lookup"><span data-stu-id="a3dee-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="a3dee-103">取得可讓 common language runtime (CLR) 管理身分識別的介面指標。</span><span class="sxs-lookup"><span data-stu-id="a3dee-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="a3dee-104">此函式已被取代，在.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="a3dee-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3dee-105">語法</span><span class="sxs-lookup"><span data-stu-id="a3dee-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3dee-106">參數</span><span class="sxs-lookup"><span data-stu-id="a3dee-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="a3dee-107">[in]A `REFIID` （介面識別項），指定要取得的介面。</span><span class="sxs-lookup"><span data-stu-id="a3dee-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="a3dee-108">此值必須是 IID_ICLRAssemblyIdentityManager 或 IID_ICLRHostBindingPolicyManager。</span><span class="sxs-lookup"><span data-stu-id="a3dee-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="a3dee-109">[out]任一個的位址指標[ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)該[ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="a3dee-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3dee-110">備註</span><span class="sxs-lookup"><span data-stu-id="a3dee-110">Remarks</span></span>  
 <span data-ttu-id="a3dee-111">呼叫[GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)函式可取得的指標`GetCLRIdentityManager`函式。</span><span class="sxs-lookup"><span data-stu-id="a3dee-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3dee-112">需求</span><span class="sxs-lookup"><span data-stu-id="a3dee-112">Requirements</span></span>  
 <span data-ttu-id="a3dee-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3dee-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3dee-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3dee-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3dee-115">**LIBRARY:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="a3dee-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="a3dee-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3dee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3dee-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3dee-117">See also</span></span>

- [<span data-ttu-id="a3dee-118">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="a3dee-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
