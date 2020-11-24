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
ms.openlocfilehash: c155373f7da47e904c94a44efa2fba42309d4218
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671352"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="03bca-102">CorNativeLinkType 列舉</span><span class="sxs-lookup"><span data-stu-id="03bca-102">CorNativeLinkType Enumeration</span></span>

<span data-ttu-id="03bca-103">提供值，這些值表示機器碼中已連結的類型。</span><span class="sxs-lookup"><span data-stu-id="03bca-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03bca-104">語法</span><span class="sxs-lookup"><span data-stu-id="03bca-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="03bca-105">成員</span><span class="sxs-lookup"><span data-stu-id="03bca-105">Members</span></span>  
  
|<span data-ttu-id="03bca-106">member</span><span class="sxs-lookup"><span data-stu-id="03bca-106">Member</span></span>|<span data-ttu-id="03bca-107">描述</span><span class="sxs-lookup"><span data-stu-id="03bca-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="03bca-108">指出未指定任何關鍵字。</span><span class="sxs-lookup"><span data-stu-id="03bca-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="03bca-109">表示已指定 ANSI 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="03bca-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="03bca-110">指出指定了 Unicode 關鍵字</span><span class="sxs-lookup"><span data-stu-id="03bca-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="03bca-111">表示已指定 auto 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="03bca-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="03bca-112">表示已指定 OLE 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="03bca-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="03bca-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="03bca-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03bca-114">需求</span><span class="sxs-lookup"><span data-stu-id="03bca-114">Requirements</span></span>  

 <span data-ttu-id="03bca-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03bca-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03bca-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="03bca-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03bca-117">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="03bca-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03bca-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03bca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03bca-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03bca-119">See also</span></span>

- [<span data-ttu-id="03bca-120">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="03bca-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
