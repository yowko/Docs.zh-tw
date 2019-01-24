---
title: CorNativeLinkFlags 列舉
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf0fdb1e46bfbd17505e255d539547a00eb4764c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694551"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="6f4e5-102">CorNativeLinkFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="6f4e5-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="6f4e5-103">提供連結器在連結機器碼時所使用的旗標值。</span><span class="sxs-lookup"><span data-stu-id="6f4e5-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f4e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f4e5-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="6f4e5-105">成員</span><span class="sxs-lookup"><span data-stu-id="6f4e5-105">Members</span></span>  
  
|<span data-ttu-id="6f4e5-106">成員</span><span class="sxs-lookup"><span data-stu-id="6f4e5-106">Member</span></span>|<span data-ttu-id="6f4e5-107">描述</span><span class="sxs-lookup"><span data-stu-id="6f4e5-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="6f4e5-108">表示沒有旗標。</span><span class="sxs-lookup"><span data-stu-id="6f4e5-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="6f4e5-109">指出`setLastError`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6f4e5-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="6f4e5-110">指出`nomangle`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6f4e5-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="6f4e5-111">未使用。</span><span class="sxs-lookup"><span data-stu-id="6f4e5-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f4e5-112">需求</span><span class="sxs-lookup"><span data-stu-id="6f4e5-112">Requirements</span></span>  
 <span data-ttu-id="6f4e5-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f4e5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f4e5-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6f4e5-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f4e5-115">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6f4e5-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f4e5-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f4e5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f4e5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f4e5-117">See also</span></span>
- [<span data-ttu-id="6f4e5-118">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="6f4e5-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
