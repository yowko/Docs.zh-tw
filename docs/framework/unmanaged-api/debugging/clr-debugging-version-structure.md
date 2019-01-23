---
title: CLR_DEBUGGING_VERSION 結構
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4049b0ed25d4c0fda00fe9b0dad5887fa4f6996
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506936"
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="9eced-102">CLR_DEBUGGING_VERSION 結構</span><span class="sxs-lookup"><span data-stu-id="9eced-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="9eced-103">定義用來偵錯之工具通用語言執行平台 (CLR) 的產品版本。</span><span class="sxs-lookup"><span data-stu-id="9eced-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eced-104">語法</span><span class="sxs-lookup"><span data-stu-id="9eced-104">Syntax</span></span>  
  
```  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a><span data-ttu-id="9eced-105">成員</span><span class="sxs-lookup"><span data-stu-id="9eced-105">Members</span></span>  
  
|<span data-ttu-id="9eced-106">成員</span><span class="sxs-lookup"><span data-stu-id="9eced-106">Member</span></span>|<span data-ttu-id="9eced-107">描述</span><span class="sxs-lookup"><span data-stu-id="9eced-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="9eced-108">結構版本號碼</span><span class="sxs-lookup"><span data-stu-id="9eced-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="9eced-109">主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="9eced-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="9eced-110">次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="9eced-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="9eced-111">組建編號。</span><span class="sxs-lookup"><span data-stu-id="9eced-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="9eced-112">修訂編號。</span><span class="sxs-lookup"><span data-stu-id="9eced-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eced-113">備註</span><span class="sxs-lookup"><span data-stu-id="9eced-113">Remarks</span></span>  
 <span data-ttu-id="9eced-114">`CLR_DEBUGGING_VERSION`結構不過是 COR_VERSION 結構相同，則`CLR_DEBUGGING_VERSION`結構提供額外的結構版本 欄位 (`wStructVersion`)。</span><span class="sxs-lookup"><span data-stu-id="9eced-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="9eced-115">目前，此欄位必須設定為零。</span><span class="sxs-lookup"><span data-stu-id="9eced-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eced-116">需求</span><span class="sxs-lookup"><span data-stu-id="9eced-116">Requirements</span></span>  
 <span data-ttu-id="9eced-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9eced-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eced-118">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="9eced-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="9eced-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9eced-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9eced-120">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eced-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eced-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9eced-121">See also</span></span>
- [<span data-ttu-id="9eced-122">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="9eced-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="9eced-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="9eced-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
