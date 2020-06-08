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
ms.openlocfilehash: cc8b7a3174502471debf1d28725ed26c847eeb69
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500789"
---
# <a name="cor_prf_runtime_type-enumeration"></a><span data-ttu-id="0740f-102">COR_PRF_RUNTIME_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="0740f-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="0740f-103">包含值，指出在 Silverlight 中使用的 common language runtime （CLR）版本： desktop 或 CoreCLR。</span><span class="sxs-lookup"><span data-stu-id="0740f-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0740f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0740f-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="0740f-105">成員</span><span class="sxs-lookup"><span data-stu-id="0740f-105">Members</span></span>  
  
|<span data-ttu-id="0740f-106">成員</span><span class="sxs-lookup"><span data-stu-id="0740f-106">Member</span></span>|<span data-ttu-id="0740f-107">說明</span><span class="sxs-lookup"><span data-stu-id="0740f-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="0740f-108">CLR 的桌上出版本。</span><span class="sxs-lookup"><span data-stu-id="0740f-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="0740f-109">CLR 的核心版本，用於 Silverlight。</span><span class="sxs-lookup"><span data-stu-id="0740f-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0740f-110">備註</span><span class="sxs-lookup"><span data-stu-id="0740f-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0740f-111">需求</span><span class="sxs-lookup"><span data-stu-id="0740f-111">Requirements</span></span>  
 <span data-ttu-id="0740f-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0740f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0740f-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0740f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0740f-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0740f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0740f-115">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0740f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0740f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0740f-116">See also</span></span>

- [<span data-ttu-id="0740f-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="0740f-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
