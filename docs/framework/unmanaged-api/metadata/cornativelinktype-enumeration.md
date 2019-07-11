---
title: CorNativeLinkType 列舉
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 944c641c39ddef7add0e9f382dc7d35068668455
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781724"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="1ed9d-102">CorNativeLinkType 列舉</span><span class="sxs-lookup"><span data-stu-id="1ed9d-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="1ed9d-103">提供值，這些值表示機器碼中已連結的類型。</span><span class="sxs-lookup"><span data-stu-id="1ed9d-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ed9d-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ed9d-104">Syntax</span></span>  
  
```cpp  
typedef enum   
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a><span data-ttu-id="1ed9d-105">成員</span><span class="sxs-lookup"><span data-stu-id="1ed9d-105">Members</span></span>  
  
|<span data-ttu-id="1ed9d-106">成員</span><span class="sxs-lookup"><span data-stu-id="1ed9d-106">Member</span></span>|<span data-ttu-id="1ed9d-107">說明</span><span class="sxs-lookup"><span data-stu-id="1ed9d-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="1ed9d-108">表示未指定任何關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1ed9d-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="1ed9d-109">表示指定 ANSI 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1ed9d-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="1ed9d-110">表示指定的 Unicode 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1ed9d-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="1ed9d-111">表示指定 auto 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1ed9d-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="1ed9d-112">表示指定之 OLE 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1ed9d-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="1ed9d-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="1ed9d-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ed9d-114">需求</span><span class="sxs-lookup"><span data-stu-id="1ed9d-114">Requirements</span></span>  
 <span data-ttu-id="1ed9d-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ed9d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ed9d-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1ed9d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ed9d-117">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1ed9d-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ed9d-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ed9d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed9d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ed9d-119">See also</span></span>

- [<span data-ttu-id="1ed9d-120">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="1ed9d-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
