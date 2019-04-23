---
title: ICLRValidator 介面
ms.date: 03/30/2017
api_name:
- ICLRValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator
helpviewer_keywords:
- ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05287d3674e55a87cfe359fc08f74fa46000d79f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075843"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="93e2b-102">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="93e2b-102">ICLRValidator Interface</span></span>
<span data-ttu-id="93e2b-103">提供方法來驗證的可攜式執行檔 (PE) 映像和報告驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="93e2b-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93e2b-104">方法</span><span class="sxs-lookup"><span data-stu-id="93e2b-104">Methods</span></span>  
  
|<span data-ttu-id="93e2b-105">方法</span><span class="sxs-lookup"><span data-stu-id="93e2b-105">Method</span></span>|<span data-ttu-id="93e2b-106">描述</span><span class="sxs-lookup"><span data-stu-id="93e2b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93e2b-107">FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="93e2b-107">FormatEventInfo Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="93e2b-108">取得有關指定之驗證錯誤的詳細的訊息。</span><span class="sxs-lookup"><span data-stu-id="93e2b-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="93e2b-109">Validate 方法</span><span class="sxs-lookup"><span data-stu-id="93e2b-109">Validate Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)|<span data-ttu-id="93e2b-110">驗證的可攜式執行檔或 Microsoft intermediate language (MSIL)，在指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="93e2b-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93e2b-111">需求</span><span class="sxs-lookup"><span data-stu-id="93e2b-111">Requirements</span></span>  
 <span data-ttu-id="93e2b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93e2b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93e2b-113">**標頭：** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="93e2b-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="93e2b-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="93e2b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93e2b-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93e2b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93e2b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93e2b-116">See also</span></span>

- [<span data-ttu-id="93e2b-117">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="93e2b-117">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="93e2b-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="93e2b-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="93e2b-119">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="93e2b-119">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
