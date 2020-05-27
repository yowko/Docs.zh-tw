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
ms.openlocfilehash: d5eb225241f597baf7a0a5584f4aaf8bf8411ea2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009466"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="a2dca-102">ValidatorFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="a2dca-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="a2dca-103">包含值，指出應該在呼叫[ICLRValidator：： Validate](iclrvalidator-validate-method.md)方法時執行的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="a2dca-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2dca-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2dca-104">Syntax</span></span>  
  
```cpp  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="a2dca-105">成員</span><span class="sxs-lookup"><span data-stu-id="a2dca-105">Members</span></span>  
  
|<span data-ttu-id="a2dca-106">成員</span><span class="sxs-lookup"><span data-stu-id="a2dca-106">Member</span></span>|<span data-ttu-id="a2dca-107">描述</span><span class="sxs-lookup"><span data-stu-id="a2dca-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="a2dca-108">指定只應驗證可執行檔中的 Microsoft 中繼語言（MSIL）。</span><span class="sxs-lookup"><span data-stu-id="a2dca-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="a2dca-109">指定只應驗證可執行檔的格式。</span><span class="sxs-lookup"><span data-stu-id="a2dca-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="a2dca-110">指定應該在上執行和報告所有類型的驗證。</span><span class="sxs-lookup"><span data-stu-id="a2dca-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="a2dca-111">指定不應驗證可執行檔的格式。</span><span class="sxs-lookup"><span data-stu-id="a2dca-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="a2dca-112">指定驗證錯誤訊息應包含引發驗證錯誤的源程式碼。</span><span class="sxs-lookup"><span data-stu-id="a2dca-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="a2dca-113">此域值在 .NET Framework 版本2.0 中無效。</span><span class="sxs-lookup"><span data-stu-id="a2dca-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a2dca-114">需求</span><span class="sxs-lookup"><span data-stu-id="a2dca-114">Requirements</span></span>  
 <span data-ttu-id="a2dca-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2dca-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2dca-116">**標頭：** IValidator .idl，IValidator。h</span><span class="sxs-lookup"><span data-stu-id="a2dca-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="a2dca-117">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="a2dca-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2dca-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2dca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2dca-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2dca-119">See also</span></span>

- [<span data-ttu-id="a2dca-120">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="a2dca-120">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="a2dca-121">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="a2dca-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
