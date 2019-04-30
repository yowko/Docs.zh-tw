---
title: ICLRHostProtectionManager 介面
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd096344c987d8901f0baab86e370abbb03528e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61944660"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="5c44b-102">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="5c44b-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="5c44b-103">可讓主應用程式封鎖特定的 managed 的類別、 方法、 屬性和欄位，無法在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="5c44b-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c44b-104">方法</span><span class="sxs-lookup"><span data-stu-id="5c44b-104">Methods</span></span>  
  
|<span data-ttu-id="5c44b-105">方法</span><span class="sxs-lookup"><span data-stu-id="5c44b-105">Method</span></span>|<span data-ttu-id="5c44b-106">描述</span><span class="sxs-lookup"><span data-stu-id="5c44b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c44b-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="5c44b-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="5c44b-108">可提供保證，可能會導致嚴重的 common language runtime (CLR) 錯誤特定罕見的競爭條件將會永遠不會發生。</span><span class="sxs-lookup"><span data-stu-id="5c44b-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="5c44b-109">SetProtectedCategories 方法</span><span class="sxs-lookup"><span data-stu-id="5c44b-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="5c44b-110">指定的 managed 的類型和成員應該遭封鎖而無法在部分信任程式碼中執行的分類。</span><span class="sxs-lookup"><span data-stu-id="5c44b-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5c44b-111">需求</span><span class="sxs-lookup"><span data-stu-id="5c44b-111">Requirements</span></span>  
 <span data-ttu-id="5c44b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c44b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c44b-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c44b-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c44b-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5c44b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c44b-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c44b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c44b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c44b-116">See also</span></span>

- [<span data-ttu-id="5c44b-117">EApiCategories 列舉</span><span class="sxs-lookup"><span data-stu-id="5c44b-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="5c44b-118">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="5c44b-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
