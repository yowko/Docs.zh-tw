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
ms.openlocfilehash: 6a0672196ebaea5c91139851b89a7476ff6363b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430791"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="2d4fd-102">GetCLRIdentityManager 函式</span><span class="sxs-lookup"><span data-stu-id="2d4fd-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="2d4fd-103">取得可讓 common language runtime (CLR) 來管理身分識別的介面指標。</span><span class="sxs-lookup"><span data-stu-id="2d4fd-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="2d4fd-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2d4fd-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d4fd-105">語法</span><span class="sxs-lookup"><span data-stu-id="2d4fd-105">Syntax</span></span>  
  
```  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d4fd-106">參數</span><span class="sxs-lookup"><span data-stu-id="2d4fd-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="2d4fd-107">[in]A `REFIID` （介面識別項），指定要取得的介面。</span><span class="sxs-lookup"><span data-stu-id="2d4fd-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="2d4fd-108">此值必須是 IID_ICLRAssemblyIdentityManager 或 IID_ICLRHostBindingPolicyManager。</span><span class="sxs-lookup"><span data-stu-id="2d4fd-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="2d4fd-109">[out]中的其中一個位址的指標[ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)或[ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="2d4fd-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d4fd-110">備註</span><span class="sxs-lookup"><span data-stu-id="2d4fd-110">Remarks</span></span>  
 <span data-ttu-id="2d4fd-111">呼叫[GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)函式可取得的指標`GetCLRIdentityManager`函式。</span><span class="sxs-lookup"><span data-stu-id="2d4fd-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d4fd-112">需求</span><span class="sxs-lookup"><span data-stu-id="2d4fd-112">Requirements</span></span>  
 <span data-ttu-id="2d4fd-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d4fd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d4fd-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d4fd-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d4fd-115">**程式庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="2d4fd-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="2d4fd-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d4fd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d4fd-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d4fd-117">See Also</span></span>  
 [<span data-ttu-id="2d4fd-118">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="2d4fd-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
