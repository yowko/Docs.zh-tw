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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 841b05ca1037d82046820554878d883f94687d34
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779142"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="fd8cf-102">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="fd8cf-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="fd8cf-103">提供介面來管理執行程式碼執行階段。</span><span class="sxs-lookup"><span data-stu-id="fd8cf-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd8cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd8cf-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="fd8cf-105">介面</span><span class="sxs-lookup"><span data-stu-id="fd8cf-105">Interfaces</span></span>  
  
|<span data-ttu-id="fd8cf-106">介面</span><span class="sxs-lookup"><span data-stu-id="fd8cf-106">Interface</span></span>|<span data-ttu-id="fd8cf-107">描述</span><span class="sxs-lookup"><span data-stu-id="fd8cf-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="fd8cf-108">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="fd8cf-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="fd8cf-109">提供方法來控制執行階段應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="fd8cf-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="fd8cf-110">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="fd8cf-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="fd8cf-111">提供用於驗證的可攜式執行檔的影像及詳細的報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="fd8cf-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd8cf-112">需求</span><span class="sxs-lookup"><span data-stu-id="fd8cf-112">Requirements</span></span>  
 <span data-ttu-id="fd8cf-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd8cf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd8cf-114">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="fd8cf-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="fd8cf-115">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fd8cf-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd8cf-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd8cf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd8cf-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd8cf-117">See also</span></span>

- [<span data-ttu-id="fd8cf-118">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="fd8cf-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
