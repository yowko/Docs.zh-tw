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
ms.openlocfilehash: 6e40f08a3dae6f17617e97e07a23b9d7eb611083
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558627"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="dcc5c-102">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="dcc5c-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="dcc5c-103">提供介面來管理執行程式碼執行階段。</span><span class="sxs-lookup"><span data-stu-id="dcc5c-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcc5c-104">語法</span><span class="sxs-lookup"><span data-stu-id="dcc5c-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="dcc5c-105">介面</span><span class="sxs-lookup"><span data-stu-id="dcc5c-105">Interfaces</span></span>  
  
|<span data-ttu-id="dcc5c-106">介面</span><span class="sxs-lookup"><span data-stu-id="dcc5c-106">Interface</span></span>|<span data-ttu-id="dcc5c-107">描述</span><span class="sxs-lookup"><span data-stu-id="dcc5c-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="dcc5c-108">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="dcc5c-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="dcc5c-109">提供方法來控制執行階段應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="dcc5c-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="dcc5c-110">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="dcc5c-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="dcc5c-111">提供用於驗證的可攜式執行檔的影像及詳細的報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="dcc5c-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dcc5c-112">需求</span><span class="sxs-lookup"><span data-stu-id="dcc5c-112">Requirements</span></span>  
 <span data-ttu-id="dcc5c-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dcc5c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcc5c-114">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="dcc5c-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="dcc5c-115">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dcc5c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcc5c-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcc5c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc5c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcc5c-117">See also</span></span>
- [<span data-ttu-id="dcc5c-118">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="dcc5c-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
