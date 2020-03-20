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
ms.openlocfilehash: 8fe6216e11a64ea182d796247d888b862b1e8377
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177933"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="5ca4e-102">CorRegFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="5ca4e-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="5ca4e-103">提供安裝模組或複合映射時用於註冊的標誌值。</span><span class="sxs-lookup"><span data-stu-id="5ca4e-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ca4e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5ca4e-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="5ca4e-105">成員</span><span class="sxs-lookup"><span data-stu-id="5ca4e-105">Members</span></span>  
  
|<span data-ttu-id="5ca4e-106">member</span><span class="sxs-lookup"><span data-stu-id="5ca4e-106">Member</span></span>|<span data-ttu-id="5ca4e-107">描述</span><span class="sxs-lookup"><span data-stu-id="5ca4e-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="5ca4e-108">指定不應將檔案複製到目標。</span><span class="sxs-lookup"><span data-stu-id="5ca4e-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="5ca4e-109">指定模組或複合是配置。</span><span class="sxs-lookup"><span data-stu-id="5ca4e-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="5ca4e-110">指定模組或複合具有類引用。</span><span class="sxs-lookup"><span data-stu-id="5ca4e-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5ca4e-111">需求</span><span class="sxs-lookup"><span data-stu-id="5ca4e-111">Requirements</span></span>  
 <span data-ttu-id="5ca4e-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5ca4e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ca4e-113">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="5ca4e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ca4e-114">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="5ca4e-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5ca4e-115">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ca4e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca4e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ca4e-116">See also</span></span>

- [<span data-ttu-id="5ca4e-117">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="5ca4e-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
