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
ms.openlocfilehash: 1a732e59d539c330f91e8665e81dc4771b40e2d0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123291"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="cf544-102">IValidator 介面</span><span class="sxs-lookup"><span data-stu-id="cf544-102">IValidator Interface</span></span>
<span data-ttu-id="cf544-103">提供驗證可移植執行檔（PE）映射和報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="cf544-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf544-104">方法</span><span class="sxs-lookup"><span data-stu-id="cf544-104">Methods</span></span>  
  
|<span data-ttu-id="cf544-105">方法</span><span class="sxs-lookup"><span data-stu-id="cf544-105">Method</span></span>|<span data-ttu-id="cf544-106">描述</span><span class="sxs-lookup"><span data-stu-id="cf544-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cf544-107">Validate</span><span class="sxs-lookup"><span data-stu-id="cf544-107">Validate</span></span>|<span data-ttu-id="cf544-108">驗證指定的 PE 或 Microsoft 中繼語言（MSIL）檔案。</span><span class="sxs-lookup"><span data-stu-id="cf544-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="cf544-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="cf544-109">FormatEventInfo</span></span>|<span data-ttu-id="cf544-110">取得對應于指定驗證錯誤的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="cf544-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf544-111">需求</span><span class="sxs-lookup"><span data-stu-id="cf544-111">Requirements</span></span>  
 <span data-ttu-id="cf544-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf544-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf544-113">**標頭：** IValidator .idl，IValidator。h</span><span class="sxs-lookup"><span data-stu-id="cf544-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="cf544-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cf544-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf544-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf544-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf544-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="cf544-116">See also</span></span>

- [<span data-ttu-id="cf544-117">裝載介面</span><span class="sxs-lookup"><span data-stu-id="cf544-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="cf544-118">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="cf544-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
