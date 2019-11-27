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
ms.openlocfilehash: 79a9e4513a98a29edc11cc76c599f03c9c3a72b4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450107"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="bad9a-102">CorRegFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="bad9a-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="bad9a-103">提供安裝模組或複合影像時，用來註冊的旗標值。</span><span class="sxs-lookup"><span data-stu-id="bad9a-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bad9a-104">語法</span><span class="sxs-lookup"><span data-stu-id="bad9a-104">Syntax</span></span>  
  
```cpp  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="bad9a-105">Members</span><span class="sxs-lookup"><span data-stu-id="bad9a-105">Members</span></span>  
  
|<span data-ttu-id="bad9a-106">成員</span><span class="sxs-lookup"><span data-stu-id="bad9a-106">Member</span></span>|<span data-ttu-id="bad9a-107">描述</span><span class="sxs-lookup"><span data-stu-id="bad9a-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="bad9a-108">指定不應該將檔案複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="bad9a-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="bad9a-109">指定模組或複合為設定。</span><span class="sxs-lookup"><span data-stu-id="bad9a-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="bad9a-110">指定模組或複合具有類別參考。</span><span class="sxs-lookup"><span data-stu-id="bad9a-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bad9a-111">需求</span><span class="sxs-lookup"><span data-stu-id="bad9a-111">Requirements</span></span>  
 <span data-ttu-id="bad9a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bad9a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bad9a-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="bad9a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bad9a-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bad9a-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bad9a-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bad9a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad9a-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="bad9a-116">See also</span></span>

- [<span data-ttu-id="bad9a-117">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="bad9a-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
