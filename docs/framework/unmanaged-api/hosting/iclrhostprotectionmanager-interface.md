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
ms.openlocfilehash: 0487a87420c888cf5466f54c28c2d89623260add
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141058"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="2c3f1-102">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="2c3f1-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="2c3f1-103">可讓主機封鎖特定的 managed 類別、方法、屬性和欄位，使其無法在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="2c3f1-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c3f1-104">方法</span><span class="sxs-lookup"><span data-stu-id="2c3f1-104">Methods</span></span>  
  
|<span data-ttu-id="2c3f1-105">方法</span><span class="sxs-lookup"><span data-stu-id="2c3f1-105">Method</span></span>|<span data-ttu-id="2c3f1-106">描述</span><span class="sxs-lookup"><span data-stu-id="2c3f1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c3f1-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="2c3f1-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="2c3f1-108">提供保證不會引發嚴重 common language runtime （CLR）錯誤的特定罕見競爭條件。</span><span class="sxs-lookup"><span data-stu-id="2c3f1-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="2c3f1-109">SetProtectedCategories 方法</span><span class="sxs-lookup"><span data-stu-id="2c3f1-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="2c3f1-110">指定應該封鎖在部分信任程式碼中執行之 managed 類型和成員的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="2c3f1-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c3f1-111">需求</span><span class="sxs-lookup"><span data-stu-id="2c3f1-111">Requirements</span></span>  
 <span data-ttu-id="2c3f1-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c3f1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c3f1-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2c3f1-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c3f1-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2c3f1-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c3f1-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c3f1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3f1-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="2c3f1-116">See also</span></span>

- [<span data-ttu-id="2c3f1-117">EApiCategories 列舉</span><span class="sxs-lookup"><span data-stu-id="2c3f1-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="2c3f1-118">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="2c3f1-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
