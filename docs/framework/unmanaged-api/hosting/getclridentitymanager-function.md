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
ms.openlocfilehash: 9d1196749e033c71b0c8923d0325eb4886122d1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733655"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="9f759-102">GetCLRIdentityManager 函式</span><span class="sxs-lookup"><span data-stu-id="9f759-102">GetCLRIdentityManager Function</span></span>

<span data-ttu-id="9f759-103">取得介面的指標，該介面可讓 common language runtime (CLR) 管理身分識別。</span><span class="sxs-lookup"><span data-stu-id="9f759-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="9f759-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="9f759-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f759-105">語法</span><span class="sxs-lookup"><span data-stu-id="9f759-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f759-106">參數</span><span class="sxs-lookup"><span data-stu-id="9f759-106">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="9f759-107">在 `REFIID` (介面識別碼) ，可指定要取得的介面。</span><span class="sxs-lookup"><span data-stu-id="9f759-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="9f759-108">此值必須是 IID_ICLRAssemblyIdentityManager 或 IID_ICLRHostBindingPolicyManager。</span><span class="sxs-lookup"><span data-stu-id="9f759-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="9f759-109">擴展 [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) 或 [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="9f759-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f759-110">備註</span><span class="sxs-lookup"><span data-stu-id="9f759-110">Remarks</span></span>  

 <span data-ttu-id="9f759-111">呼叫 [GetRealProcAddress](getrealprocaddress-function.md) 函式來取得函式的指標 `GetCLRIdentityManager` 。</span><span class="sxs-lookup"><span data-stu-id="9f759-111">Call the [GetRealProcAddress](getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f759-112">需求</span><span class="sxs-lookup"><span data-stu-id="9f759-112">Requirements</span></span>  

 <span data-ttu-id="9f759-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9f759-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f759-114">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9f759-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f759-115">連結 **庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="9f759-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="9f759-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f759-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f759-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f759-117">See also</span></span>

- [<span data-ttu-id="9f759-118">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="9f759-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
