---
title: "IValidator 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator
api_location: mscoree.dll
api_type: COM
f1_keywords: IValidator
helpviewer_keywords: IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1afa255fa0b1baec35dbd8aa6e0beef62d240c31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ivalidator-interface"></a><span data-ttu-id="a5508-102">IValidator 介面</span><span class="sxs-lookup"><span data-stu-id="a5508-102">IValidator Interface</span></span>
<span data-ttu-id="a5508-103">提供方法來驗證的可攜式執行檔 (PE) 影像，以及回報驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="a5508-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5508-104">方法</span><span class="sxs-lookup"><span data-stu-id="a5508-104">Methods</span></span>  
  
|<span data-ttu-id="a5508-105">方法</span><span class="sxs-lookup"><span data-stu-id="a5508-105">Method</span></span>|<span data-ttu-id="a5508-106">描述</span><span class="sxs-lookup"><span data-stu-id="a5508-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a5508-107">Validate</span><span class="sxs-lookup"><span data-stu-id="a5508-107">Validate</span></span>|<span data-ttu-id="a5508-108">驗證指定的 PE 或 Microsoft 中繼語言 (MSIL) 檔案。</span><span class="sxs-lookup"><span data-stu-id="a5508-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="a5508-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="a5508-109">FormatEventInfo</span></span>|<span data-ttu-id="a5508-110">取得對應至指定的驗證錯誤的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a5508-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5508-111">需求</span><span class="sxs-lookup"><span data-stu-id="a5508-111">Requirements</span></span>  
 <span data-ttu-id="a5508-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5508-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5508-113">**標頭：** IValidator.idl、 IValidator.h</span><span class="sxs-lookup"><span data-stu-id="a5508-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="a5508-114">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a5508-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5508-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5508-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5508-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="a5508-116">See Also</span></span>  
 [<span data-ttu-id="a5508-117">裝載介面</span><span class="sxs-lookup"><span data-stu-id="a5508-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="a5508-118">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="a5508-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
