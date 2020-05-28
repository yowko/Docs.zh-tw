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
ms.openlocfilehash: d8e5ab607f9310341ded482b35f02f3845926328
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008556"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="7d779-102">IValidator 介面</span><span class="sxs-lookup"><span data-stu-id="7d779-102">IValidator Interface</span></span>
<span data-ttu-id="7d779-103">提供驗證可移植執行檔（PE）映射和報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="7d779-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d779-104">方法</span><span class="sxs-lookup"><span data-stu-id="7d779-104">Methods</span></span>  
  
|<span data-ttu-id="7d779-105">方法</span><span class="sxs-lookup"><span data-stu-id="7d779-105">Method</span></span>|<span data-ttu-id="7d779-106">描述</span><span class="sxs-lookup"><span data-stu-id="7d779-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7d779-107">驗證</span><span class="sxs-lookup"><span data-stu-id="7d779-107">Validate</span></span>|<span data-ttu-id="7d779-108">驗證指定的 PE 或 Microsoft 中繼語言（MSIL）檔案。</span><span class="sxs-lookup"><span data-stu-id="7d779-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="7d779-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="7d779-109">FormatEventInfo</span></span>|<span data-ttu-id="7d779-110">取得對應于指定驗證錯誤的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="7d779-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d779-111">需求</span><span class="sxs-lookup"><span data-stu-id="7d779-111">Requirements</span></span>  
 <span data-ttu-id="7d779-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7d779-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d779-113">**標頭：** IValidator .idl，IValidator。h</span><span class="sxs-lookup"><span data-stu-id="7d779-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="7d779-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7d779-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d779-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d779-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d779-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d779-116">See also</span></span>

- [<span data-ttu-id="7d779-117">裝載介面</span><span class="sxs-lookup"><span data-stu-id="7d779-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="7d779-118">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="7d779-118">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
