---
title: ValidatorFlags 列舉
ms.date: 03/30/2017
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20ce52108c1024ad3e07051b226aa65612580e2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441384"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="7d687-102">ValidatorFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="7d687-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="7d687-103">包含值，表示應該執行的呼叫中的驗證類型[iclrvalidator:: Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="7d687-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d687-104">語法</span><span class="sxs-lookup"><span data-stu-id="7d687-104">Syntax</span></span>  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="7d687-105">成員</span><span class="sxs-lookup"><span data-stu-id="7d687-105">Members</span></span>  
  
|<span data-ttu-id="7d687-106">成員</span><span class="sxs-lookup"><span data-stu-id="7d687-106">Member</span></span>|<span data-ttu-id="7d687-107">描述</span><span class="sxs-lookup"><span data-stu-id="7d687-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="7d687-108">指定應該驗證只的 Microsoft intermediate language (MSIL) 中的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="7d687-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="7d687-109">指定應該驗證可執行檔的格式。</span><span class="sxs-lookup"><span data-stu-id="7d687-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="7d687-110">指定應該執行所有類型的驗證及報告。</span><span class="sxs-lookup"><span data-stu-id="7d687-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="7d687-111">指定不驗證可執行檔的格式。</span><span class="sxs-lookup"><span data-stu-id="7d687-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="7d687-112">指定的驗證錯誤訊息應該包括發生驗證錯誤的原始程式碼字行。</span><span class="sxs-lookup"><span data-stu-id="7d687-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="7d687-113">.NET Framework 2.0 版中，這個欄位的值無效。</span><span class="sxs-lookup"><span data-stu-id="7d687-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d687-114">需求</span><span class="sxs-lookup"><span data-stu-id="7d687-114">Requirements</span></span>  
 <span data-ttu-id="7d687-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7d687-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d687-116">**標頭：** IValidator.idl、 IValidator.h</span><span class="sxs-lookup"><span data-stu-id="7d687-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="7d687-117">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d687-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d687-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d687-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d687-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d687-119">See Also</span></span>  
 [<span data-ttu-id="7d687-120">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="7d687-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="7d687-121">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="7d687-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
