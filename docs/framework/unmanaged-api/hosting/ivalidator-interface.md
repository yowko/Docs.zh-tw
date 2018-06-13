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
ms.openlocfilehash: 9e79a69bf71aee035fb1f9a0178879d7c19e62b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448917"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="426c2-102">IValidator 介面</span><span class="sxs-lookup"><span data-stu-id="426c2-102">IValidator Interface</span></span>
<span data-ttu-id="426c2-103">提供方法來驗證的可攜式執行檔 (PE) 影像，以及回報驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="426c2-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="426c2-104">方法</span><span class="sxs-lookup"><span data-stu-id="426c2-104">Methods</span></span>  
  
|<span data-ttu-id="426c2-105">方法</span><span class="sxs-lookup"><span data-stu-id="426c2-105">Method</span></span>|<span data-ttu-id="426c2-106">描述</span><span class="sxs-lookup"><span data-stu-id="426c2-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="426c2-107">Validate</span><span class="sxs-lookup"><span data-stu-id="426c2-107">Validate</span></span>|<span data-ttu-id="426c2-108">驗證指定的 PE 或 Microsoft 中繼語言 (MSIL) 檔案。</span><span class="sxs-lookup"><span data-stu-id="426c2-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="426c2-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="426c2-109">FormatEventInfo</span></span>|<span data-ttu-id="426c2-110">取得對應至指定的驗證錯誤的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="426c2-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="426c2-111">需求</span><span class="sxs-lookup"><span data-stu-id="426c2-111">Requirements</span></span>  
 <span data-ttu-id="426c2-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="426c2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="426c2-113">**標頭：** IValidator.idl、 IValidator.h</span><span class="sxs-lookup"><span data-stu-id="426c2-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="426c2-114">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="426c2-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="426c2-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="426c2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="426c2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="426c2-116">See Also</span></span>  
 [<span data-ttu-id="426c2-117">裝載介面</span><span class="sxs-lookup"><span data-stu-id="426c2-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="426c2-118">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="426c2-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
