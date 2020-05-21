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
ms.openlocfilehash: e071f9cba7e991c59bf697647e0e4badea57573a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762028"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="e64ee-102">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="e64ee-102">ICLRValidator Interface</span></span>
<span data-ttu-id="e64ee-103">提供驗證可移植執行檔（PE）映射和報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="e64ee-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e64ee-104">方法</span><span class="sxs-lookup"><span data-stu-id="e64ee-104">Methods</span></span>  
  
|<span data-ttu-id="e64ee-105">方法</span><span class="sxs-lookup"><span data-stu-id="e64ee-105">Method</span></span>|<span data-ttu-id="e64ee-106">描述</span><span class="sxs-lookup"><span data-stu-id="e64ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e64ee-107">FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="e64ee-107">FormatEventInfo Method</span></span>](iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="e64ee-108">取得有關指定之驗證錯誤的詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="e64ee-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="e64ee-109">Validate 方法</span><span class="sxs-lookup"><span data-stu-id="e64ee-109">Validate Method</span></span>](iclrvalidator-validate-method.md)|<span data-ttu-id="e64ee-110">驗證指定檔案中的可攜式可執行檔或 Microsoft 中繼語言（MSIL）。</span><span class="sxs-lookup"><span data-stu-id="e64ee-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e64ee-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="e64ee-111">Requirements</span></span>  
 <span data-ttu-id="e64ee-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e64ee-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e64ee-113">**標頭：** IValidator .idl，IValidator。h</span><span class="sxs-lookup"><span data-stu-id="e64ee-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="e64ee-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e64ee-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e64ee-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e64ee-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e64ee-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e64ee-116">See also</span></span>

- [<span data-ttu-id="e64ee-117">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="e64ee-117">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="e64ee-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="e64ee-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="e64ee-119">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="e64ee-119">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
