---
title: CLRRuntimeHost Coclass
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
ms.openlocfilehash: 40766ce5837053493f2e3f1f25fe7d1d63ec695f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616797"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="7a41d-102">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="7a41d-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="7a41d-103">提供介面，以供運行時間管理程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="7a41d-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a41d-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a41d-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="7a41d-105">介面</span><span class="sxs-lookup"><span data-stu-id="7a41d-105">Interfaces</span></span>  
  
|<span data-ttu-id="7a41d-106">介面</span><span class="sxs-lookup"><span data-stu-id="7a41d-106">Interface</span></span>|<span data-ttu-id="7a41d-107">描述</span><span class="sxs-lookup"><span data-stu-id="7a41d-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="7a41d-108">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="7a41d-108">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)|<span data-ttu-id="7a41d-109">提供方法來控制執行時間的應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="7a41d-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="7a41d-110">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="7a41d-110">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)|<span data-ttu-id="7a41d-111">提供可移植可執行映射的驗證方法，以及詳細的驗證錯誤報表。</span><span class="sxs-lookup"><span data-stu-id="7a41d-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a41d-112">需求</span><span class="sxs-lookup"><span data-stu-id="7a41d-112">Requirements</span></span>  
 <span data-ttu-id="7a41d-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a41d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a41d-114">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="7a41d-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="7a41d-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7a41d-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a41d-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a41d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a41d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a41d-117">See also</span></span>

- [<span data-ttu-id="7a41d-118">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="7a41d-118">Hosting Coclasses</span></span>](hosting-coclasses.md)
