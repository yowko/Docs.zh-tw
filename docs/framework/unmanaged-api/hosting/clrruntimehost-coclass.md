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
ms.openlocfilehash: b1e595e1a4f1b462437f47207b998829a8bd774d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129457"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="1fe5c-102">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="1fe5c-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="1fe5c-103">提供介面，以供運行時間管理程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="1fe5c-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fe5c-104">語法</span><span class="sxs-lookup"><span data-stu-id="1fe5c-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="1fe5c-105">介面</span><span class="sxs-lookup"><span data-stu-id="1fe5c-105">Interfaces</span></span>  
  
|<span data-ttu-id="1fe5c-106">介面</span><span class="sxs-lookup"><span data-stu-id="1fe5c-106">Interface</span></span>|<span data-ttu-id="1fe5c-107">描述</span><span class="sxs-lookup"><span data-stu-id="1fe5c-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="1fe5c-108">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="1fe5c-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="1fe5c-109">提供方法來控制執行時間的應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="1fe5c-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="1fe5c-110">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="1fe5c-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="1fe5c-111">提供可移植可執行映射的驗證方法，以及詳細的驗證錯誤報表。</span><span class="sxs-lookup"><span data-stu-id="1fe5c-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1fe5c-112">需求</span><span class="sxs-lookup"><span data-stu-id="1fe5c-112">Requirements</span></span>  
 <span data-ttu-id="1fe5c-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1fe5c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fe5c-114">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="1fe5c-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="1fe5c-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1fe5c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1fe5c-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fe5c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe5c-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="1fe5c-117">See also</span></span>

- [<span data-ttu-id="1fe5c-118">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="1fe5c-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
