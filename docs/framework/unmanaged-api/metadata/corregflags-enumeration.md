---
title: CorRegFlags 列舉
ms.date: 03/30/2017
api_name:
- CorRegFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegFlags
helpviewer_keywords:
- CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb6b303fa7569712c854e8dc4e7513d8608e2519
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104958"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="5c17f-102">CorRegFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="5c17f-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="5c17f-103">提供用於註冊安裝模組或複合映像時的旗標值。</span><span class="sxs-lookup"><span data-stu-id="5c17f-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c17f-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c17f-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="5c17f-105">成員</span><span class="sxs-lookup"><span data-stu-id="5c17f-105">Members</span></span>  
  
|<span data-ttu-id="5c17f-106">成員</span><span class="sxs-lookup"><span data-stu-id="5c17f-106">Member</span></span>|<span data-ttu-id="5c17f-107">描述</span><span class="sxs-lookup"><span data-stu-id="5c17f-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="5c17f-108">指定的檔案不會複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="5c17f-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="5c17f-109">指定模組或組合的組態。</span><span class="sxs-lookup"><span data-stu-id="5c17f-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="5c17f-110">指定此模組或複合類別的參考。</span><span class="sxs-lookup"><span data-stu-id="5c17f-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5c17f-111">需求</span><span class="sxs-lookup"><span data-stu-id="5c17f-111">Requirements</span></span>  
 <span data-ttu-id="5c17f-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c17f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c17f-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5c17f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c17f-114">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5c17f-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="5c17f-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="5c17f-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5c17f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c17f-116">See also</span></span>

- [<span data-ttu-id="5c17f-117">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="5c17f-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
