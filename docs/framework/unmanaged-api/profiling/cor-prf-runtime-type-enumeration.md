---
title: COR_PRF_RUNTIME_TYPE 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_RUNTIME_TYPE Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_RUNTIME_TYPE
helpviewer_keywords:
- COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e57c622780f0bc92061fd2928ea861f904d9eb37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122105"
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="8cd37-102">COR_PRF_RUNTIME_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="8cd37-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="8cd37-103">包含值，表示 common language runtime (CLR) 版本： 桌面或 CoreCLR，Silverlight 中使用。</span><span class="sxs-lookup"><span data-stu-id="8cd37-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cd37-104">語法</span><span class="sxs-lookup"><span data-stu-id="8cd37-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="8cd37-105">成員</span><span class="sxs-lookup"><span data-stu-id="8cd37-105">Members</span></span>  
  
|<span data-ttu-id="8cd37-106">成員</span><span class="sxs-lookup"><span data-stu-id="8cd37-106">Member</span></span>|<span data-ttu-id="8cd37-107">描述</span><span class="sxs-lookup"><span data-stu-id="8cd37-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="8cd37-108">桌面 CLR 的版本。</span><span class="sxs-lookup"><span data-stu-id="8cd37-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="8cd37-109">使用 Silverlight 中的 CLR 核心版本。</span><span class="sxs-lookup"><span data-stu-id="8cd37-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cd37-110">備註</span><span class="sxs-lookup"><span data-stu-id="8cd37-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cd37-111">需求</span><span class="sxs-lookup"><span data-stu-id="8cd37-111">Requirements</span></span>  
 <span data-ttu-id="8cd37-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8cd37-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cd37-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8cd37-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8cd37-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cd37-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8cd37-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="8cd37-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8cd37-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cd37-116">See also</span></span>

- [<span data-ttu-id="8cd37-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="8cd37-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
