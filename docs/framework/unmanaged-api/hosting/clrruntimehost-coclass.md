---
title: CLRRuntimeHost Coclass
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CLRRuntimeHost
helpviewer_keywords: CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 18e4518a2e321609a8add06c399ed9588748d1ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="4e373-102">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="4e373-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="4e373-103">提供介面來管理執行階段所執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="4e373-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e373-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e373-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="4e373-105">介面</span><span class="sxs-lookup"><span data-stu-id="4e373-105">Interfaces</span></span>  
  
|<span data-ttu-id="4e373-106">介面</span><span class="sxs-lookup"><span data-stu-id="4e373-106">Interface</span></span>|<span data-ttu-id="4e373-107">描述</span><span class="sxs-lookup"><span data-stu-id="4e373-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="4e373-108">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="4e373-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="4e373-109">提供方法來控制執行階段執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e373-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="4e373-110">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="4e373-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="4e373-111">提供用於驗證的可攜式執行檔映像及詳細報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="4e373-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e373-112">需求</span><span class="sxs-lookup"><span data-stu-id="4e373-112">Requirements</span></span>  
 <span data-ttu-id="4e373-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e373-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e373-114">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="4e373-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="4e373-115">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4e373-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e373-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e373-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e373-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e373-117">See Also</span></span>  
 [<span data-ttu-id="4e373-118">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="4e373-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
