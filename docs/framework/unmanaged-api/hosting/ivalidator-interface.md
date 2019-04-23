---
title: IValidator 介面
ms.date: 03/30/2017
api_name:
- IValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IValidator
helpviewer_keywords:
- IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f516bf1f19e4d4a77e2d6af834a1c3d4e34c327
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121910"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="9a41d-102">IValidator 介面</span><span class="sxs-lookup"><span data-stu-id="9a41d-102">IValidator Interface</span></span>
<span data-ttu-id="9a41d-103">提供方法來驗證的可攜式執行檔 (PE) 映像和報告驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="9a41d-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a41d-104">方法</span><span class="sxs-lookup"><span data-stu-id="9a41d-104">Methods</span></span>  
  
|<span data-ttu-id="9a41d-105">方法</span><span class="sxs-lookup"><span data-stu-id="9a41d-105">Method</span></span>|<span data-ttu-id="9a41d-106">描述</span><span class="sxs-lookup"><span data-stu-id="9a41d-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9a41d-107">Validate</span><span class="sxs-lookup"><span data-stu-id="9a41d-107">Validate</span></span>|<span data-ttu-id="9a41d-108">驗證指定的 PE 或 Microsoft intermediate language (MSIL) 檔案。</span><span class="sxs-lookup"><span data-stu-id="9a41d-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="9a41d-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="9a41d-109">FormatEventInfo</span></span>|<span data-ttu-id="9a41d-110">取得對應至指定的驗證錯誤的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="9a41d-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a41d-111">需求</span><span class="sxs-lookup"><span data-stu-id="9a41d-111">Requirements</span></span>  
 <span data-ttu-id="9a41d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9a41d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a41d-113">**標頭：** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="9a41d-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="9a41d-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9a41d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a41d-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a41d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a41d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a41d-116">See also</span></span>

- [<span data-ttu-id="9a41d-117">裝載介面</span><span class="sxs-lookup"><span data-stu-id="9a41d-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="9a41d-118">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="9a41d-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
