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
ms.openlocfilehash: d9ccd5c6c91b1ab2166ff40a0fb2048e15927d3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723944"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="7c2ab-102">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="7c2ab-102">ICLRValidator Interface</span></span>

<span data-ttu-id="7c2ab-103">提供驗證可攜式可執行檔 (PE) 映射和報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="7c2ab-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c2ab-104">方法</span><span class="sxs-lookup"><span data-stu-id="7c2ab-104">Methods</span></span>  
  
|<span data-ttu-id="7c2ab-105">方法</span><span class="sxs-lookup"><span data-stu-id="7c2ab-105">Method</span></span>|<span data-ttu-id="7c2ab-106">描述</span><span class="sxs-lookup"><span data-stu-id="7c2ab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c2ab-107">FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="7c2ab-107">FormatEventInfo Method</span></span>](iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="7c2ab-108">取得有關指定之驗證錯誤的詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="7c2ab-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="7c2ab-109">Validate 方法</span><span class="sxs-lookup"><span data-stu-id="7c2ab-109">Validate Method</span></span>](iclrvalidator-validate-method.md)|<span data-ttu-id="7c2ab-110">驗證指定檔案中的可攜式可執行檔或 Microsoft 中繼語言 (MSIL) 。</span><span class="sxs-lookup"><span data-stu-id="7c2ab-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c2ab-111">需求</span><span class="sxs-lookup"><span data-stu-id="7c2ab-111">Requirements</span></span>  

 <span data-ttu-id="7c2ab-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c2ab-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c2ab-113">**標頭：** IValidator .idl、IValidator。h</span><span class="sxs-lookup"><span data-stu-id="7c2ab-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="7c2ab-114">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="7c2ab-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c2ab-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c2ab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c2ab-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c2ab-116">See also</span></span>

- [<span data-ttu-id="7c2ab-117">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="7c2ab-117">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="7c2ab-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="7c2ab-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="7c2ab-119">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="7c2ab-119">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
