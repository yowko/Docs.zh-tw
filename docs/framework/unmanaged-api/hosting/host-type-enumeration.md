---
title: HOST_TYPE 列舉
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
ms.openlocfilehash: cc0cea10b4a209583fb7afb551a6b80d52ad7f62
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127020"
---
# <a name="host_type-enumeration"></a><span data-ttu-id="be67f-102">HOST_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="be67f-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="be67f-103">包含值，指定啟動應用程式的主控制項類型。</span><span class="sxs-lookup"><span data-stu-id="be67f-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be67f-104">語法</span><span class="sxs-lookup"><span data-stu-id="be67f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="be67f-105">Members</span><span class="sxs-lookup"><span data-stu-id="be67f-105">Members</span></span>  
  
|<span data-ttu-id="be67f-106">成員</span><span class="sxs-lookup"><span data-stu-id="be67f-106">Member</span></span>|<span data-ttu-id="be67f-107">描述</span><span class="sxs-lookup"><span data-stu-id="be67f-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="be67f-108">從 AppLaunch 啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="be67f-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="be67f-109">對於部分信任的應用程式，請使用此值。</span><span class="sxs-lookup"><span data-stu-id="be67f-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="be67f-110">直接啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="be67f-110">Launch the application directly.</span></span> <span data-ttu-id="be67f-111">也就是從本身的 .exe 檔案啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="be67f-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="be67f-112">對於完全信任的應用程式，請使用此值。</span><span class="sxs-lookup"><span data-stu-id="be67f-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="be67f-113">與 HOST_TYPE_APPLAUNCH 相同。</span><span class="sxs-lookup"><span data-stu-id="be67f-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be67f-114">需求</span><span class="sxs-lookup"><span data-stu-id="be67f-114">Requirements</span></span>  
 <span data-ttu-id="be67f-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be67f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be67f-116">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="be67f-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be67f-117">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="be67f-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be67f-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be67f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be67f-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="be67f-119">See also</span></span>

- [<span data-ttu-id="be67f-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="be67f-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
