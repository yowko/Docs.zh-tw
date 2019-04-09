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
ms.openlocfilehash: fa10ae1cf67339a6719210f3162f19ac648e8ee5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127409"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="5cea2-102">ValidatorFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="5cea2-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="5cea2-103">包含值，表示應該執行的呼叫中的驗證類型[iclrvalidator:: Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5cea2-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cea2-104">語法</span><span class="sxs-lookup"><span data-stu-id="5cea2-104">Syntax</span></span>  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="5cea2-105">成員</span><span class="sxs-lookup"><span data-stu-id="5cea2-105">Members</span></span>  
  
|<span data-ttu-id="5cea2-106">成員</span><span class="sxs-lookup"><span data-stu-id="5cea2-106">Member</span></span>|<span data-ttu-id="5cea2-107">描述</span><span class="sxs-lookup"><span data-stu-id="5cea2-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="5cea2-108">指定只有的 Microsoft intermediate language (MSIL) 中的可執行檔應該進行驗證。</span><span class="sxs-lookup"><span data-stu-id="5cea2-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="5cea2-109">指定的可執行檔的格式進行驗證。</span><span class="sxs-lookup"><span data-stu-id="5cea2-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="5cea2-110">指定應該執行和報告的所有類型的驗證。</span><span class="sxs-lookup"><span data-stu-id="5cea2-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="5cea2-111">指定不應該驗證可執行檔的格式。</span><span class="sxs-lookup"><span data-stu-id="5cea2-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="5cea2-112">指定驗證錯誤訊息應包含的原始程式碼程式行，顯示發生驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="5cea2-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="5cea2-113">.NET Framework 2.0 版中，此欄位的值無效。</span><span class="sxs-lookup"><span data-stu-id="5cea2-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5cea2-114">需求</span><span class="sxs-lookup"><span data-stu-id="5cea2-114">Requirements</span></span>  
 <span data-ttu-id="5cea2-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5cea2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cea2-116">**標頭：** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="5cea2-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="5cea2-117">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5cea2-117">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5cea2-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="5cea2-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5cea2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cea2-119">See also</span></span>

- [<span data-ttu-id="5cea2-120">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="5cea2-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="5cea2-121">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="5cea2-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
