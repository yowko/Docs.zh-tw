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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfb1cff3e95c5ff86d22913745b7d14982766b48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175223"
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="e020f-102">HOST_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="e020f-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="e020f-103">包含指定的啟動應用程式的主機類型的值。</span><span class="sxs-lookup"><span data-stu-id="e020f-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e020f-104">語法</span><span class="sxs-lookup"><span data-stu-id="e020f-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="e020f-105">成員</span><span class="sxs-lookup"><span data-stu-id="e020f-105">Members</span></span>  
  
|<span data-ttu-id="e020f-106">成員</span><span class="sxs-lookup"><span data-stu-id="e020f-106">Member</span></span>|<span data-ttu-id="e020f-107">描述</span><span class="sxs-lookup"><span data-stu-id="e020f-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="e020f-108">啟動從 AppLaunch.exe 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e020f-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="e020f-109">部分信任的應用程式中使用此值。</span><span class="sxs-lookup"><span data-stu-id="e020f-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="e020f-110">直接啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="e020f-110">Launch the application directly.</span></span> <span data-ttu-id="e020f-111">也就是啟動應用程式與它自己的.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="e020f-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="e020f-112">使用此值為完全受信任的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e020f-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="e020f-113">HOST_TYPE_APPLAUNCH 相同。</span><span class="sxs-lookup"><span data-stu-id="e020f-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e020f-114">需求</span><span class="sxs-lookup"><span data-stu-id="e020f-114">Requirements</span></span>  
 <span data-ttu-id="e020f-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e020f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e020f-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e020f-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e020f-117">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e020f-117">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e020f-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="e020f-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e020f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e020f-119">See also</span></span>

- [<span data-ttu-id="e020f-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="e020f-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
