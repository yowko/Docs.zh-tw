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
ms.openlocfilehash: 6f34a9aac31fe50974a6f88416d0a00cd72aca8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511926"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="76dbb-102">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="76dbb-102">ICLRValidator Interface</span></span>
<span data-ttu-id="76dbb-103">提供方法來驗證的可攜式執行檔 (PE) 映像和報告驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="76dbb-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="76dbb-104">方法</span><span class="sxs-lookup"><span data-stu-id="76dbb-104">Methods</span></span>  
  
|<span data-ttu-id="76dbb-105">方法</span><span class="sxs-lookup"><span data-stu-id="76dbb-105">Method</span></span>|<span data-ttu-id="76dbb-106">描述</span><span class="sxs-lookup"><span data-stu-id="76dbb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="76dbb-107">FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="76dbb-107">FormatEventInfo Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="76dbb-108">取得有關指定之驗證錯誤的詳細的訊息。</span><span class="sxs-lookup"><span data-stu-id="76dbb-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="76dbb-109">Validate 方法</span><span class="sxs-lookup"><span data-stu-id="76dbb-109">Validate Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)|<span data-ttu-id="76dbb-110">驗證的可攜式執行檔或 Microsoft intermediate language (MSIL)，在指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="76dbb-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="76dbb-111">需求</span><span class="sxs-lookup"><span data-stu-id="76dbb-111">Requirements</span></span>  
 <span data-ttu-id="76dbb-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="76dbb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76dbb-113">**標頭：** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="76dbb-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="76dbb-114">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="76dbb-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76dbb-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76dbb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76dbb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76dbb-116">See also</span></span>
- [<span data-ttu-id="76dbb-117">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="76dbb-117">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="76dbb-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="76dbb-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="76dbb-119">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="76dbb-119">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
