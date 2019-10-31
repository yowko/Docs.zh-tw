---
title: RUNTIME_INFO_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
ms.openlocfilehash: 80643187045e7e96b9c18169c5e71287713d711f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106243"
---
# <a name="runtime_info_flags-enumeration"></a><span data-ttu-id="ea1b7-102">RUNTIME_INFO_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="ea1b7-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="ea1b7-103">包含值，指出應該傳回的通用語言執行時間（CLR）的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea1b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea1b7-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="ea1b7-105">Members</span><span class="sxs-lookup"><span data-stu-id="ea1b7-105">Members</span></span>  
  
|<span data-ttu-id="ea1b7-106">成員</span><span class="sxs-lookup"><span data-stu-id="ea1b7-106">Member</span></span>|<span data-ttu-id="ea1b7-107">描述</span><span class="sxs-lookup"><span data-stu-id="ea1b7-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="ea1b7-108">表示不應包含目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="ea1b7-109">表示不應包含版本資訊。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="ea1b7-110">表示失敗時不應顯示錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="ea1b7-111">表示應該覆寫使用 SEM_FAILCRITICALERRORS 旗標呼叫[SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242)函數的效果。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-111">Indicates that the effects of calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="ea1b7-112">也就是說，安裝對話方塊應該會在失敗時顯示，而不是隱藏。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="ea1b7-113">表示要求，以取得與 AMD-64 相容版本之執行時間的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="ea1b7-114">表示要求，以取得與 IA-64 相容版本之執行時間的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="ea1b7-115">指出與 x86 相容版本的執行時間相關資訊的要求。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="ea1b7-116">表示應該包含版本升級資訊。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea1b7-117">備註</span><span class="sxs-lookup"><span data-stu-id="ea1b7-117">Remarks</span></span>  
 <span data-ttu-id="ea1b7-118">下列平臺架構旗標一次只能指定一個，而且無法合併：</span><span class="sxs-lookup"><span data-stu-id="ea1b7-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
- <span data-ttu-id="ea1b7-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="ea1b7-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="ea1b7-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="ea1b7-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="ea1b7-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="ea1b7-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea1b7-122">需求</span><span class="sxs-lookup"><span data-stu-id="ea1b7-122">Requirements</span></span>  
 <span data-ttu-id="ea1b7-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea1b7-124">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ea1b7-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea1b7-125">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="ea1b7-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea1b7-126">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea1b7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea1b7-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea1b7-127">See also</span></span>

- [<span data-ttu-id="ea1b7-128">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="ea1b7-128">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
