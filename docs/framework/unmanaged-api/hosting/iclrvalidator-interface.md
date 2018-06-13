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
ms.openlocfilehash: 0cefd47d3c7298f9cc4b15eb2946f3d95aeae759
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437995"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="c8d4b-102">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="c8d4b-102">ICLRValidator Interface</span></span>
<span data-ttu-id="c8d4b-103">提供方法來驗證的可攜式執行檔 (PE) 影像，以及回報驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8d4b-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c8d4b-104">方法</span><span class="sxs-lookup"><span data-stu-id="c8d4b-104">Methods</span></span>  
  
|<span data-ttu-id="c8d4b-105">方法</span><span class="sxs-lookup"><span data-stu-id="c8d4b-105">Method</span></span>|<span data-ttu-id="c8d4b-106">描述</span><span class="sxs-lookup"><span data-stu-id="c8d4b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c8d4b-107">FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="c8d4b-107">FormatEventInfo Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="c8d4b-108">取得有關指定之驗證錯誤的詳細的訊息。</span><span class="sxs-lookup"><span data-stu-id="c8d4b-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="c8d4b-109">Validate 方法</span><span class="sxs-lookup"><span data-stu-id="c8d4b-109">Validate Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)|<span data-ttu-id="c8d4b-110">驗證的可攜式執行檔或 Microsoft 中繼語言 (MSIL)，在指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="c8d4b-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8d4b-111">需求</span><span class="sxs-lookup"><span data-stu-id="c8d4b-111">Requirements</span></span>  
 <span data-ttu-id="c8d4b-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8d4b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8d4b-113">**標頭：** IValidator.idl、 IValidator.h</span><span class="sxs-lookup"><span data-stu-id="c8d4b-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="c8d4b-114">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c8d4b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8d4b-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8d4b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8d4b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8d4b-116">See Also</span></span>  
 [<span data-ttu-id="c8d4b-117">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="c8d4b-117">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="c8d4b-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="c8d4b-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="c8d4b-119">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="c8d4b-119">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
