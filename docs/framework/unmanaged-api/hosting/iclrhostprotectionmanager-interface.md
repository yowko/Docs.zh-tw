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
ms.openlocfilehash: e8ead998907d55b0bfbf82e5f6f4e7c504f657ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714155"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="7f6c1-102">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="7f6c1-102">ICLRHostProtectionManager Interface</span></span>

<span data-ttu-id="7f6c1-103">讓主機封鎖特定的 managed 類別、方法、屬性和欄位，使其無法在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="7f6c1-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f6c1-104">方法</span><span class="sxs-lookup"><span data-stu-id="7f6c1-104">Methods</span></span>  
  
|<span data-ttu-id="7f6c1-105">方法</span><span class="sxs-lookup"><span data-stu-id="7f6c1-105">Method</span></span>|<span data-ttu-id="7f6c1-106">描述</span><span class="sxs-lookup"><span data-stu-id="7f6c1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f6c1-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="7f6c1-107">SetEagerSerializeGrantSets</span></span>](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="7f6c1-108">保證永遠不會發生會導致嚴重的 common language runtime (CLR) 錯誤的特定罕見競爭情形。</span><span class="sxs-lookup"><span data-stu-id="7f6c1-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="7f6c1-109">SetProtectedCategories 方法</span><span class="sxs-lookup"><span data-stu-id="7f6c1-109">SetProtectedCategories Method</span></span>](iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="7f6c1-110">指定應封鎖在部分信任程式碼中執行之 managed 類型和成員的類別。</span><span class="sxs-lookup"><span data-stu-id="7f6c1-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f6c1-111">需求</span><span class="sxs-lookup"><span data-stu-id="7f6c1-111">Requirements</span></span>  

 <span data-ttu-id="7f6c1-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f6c1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f6c1-113">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7f6c1-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f6c1-114">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="7f6c1-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f6c1-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f6c1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f6c1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f6c1-116">See also</span></span>

- [<span data-ttu-id="7f6c1-117">EApiCategories 列舉</span><span class="sxs-lookup"><span data-stu-id="7f6c1-117">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="7f6c1-118">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="7f6c1-118">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
