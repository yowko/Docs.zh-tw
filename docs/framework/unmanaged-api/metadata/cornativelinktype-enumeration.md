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
ms.openlocfilehash: 0b613ebacdff82a29fdbc3f4caa0f2b8bb5d3f6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176158"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="8dd05-102">CorNativeLinkType 列舉</span><span class="sxs-lookup"><span data-stu-id="8dd05-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="8dd05-103">提供值，這些值表示機器碼中已連結的類型。</span><span class="sxs-lookup"><span data-stu-id="8dd05-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dd05-104">語法</span><span class="sxs-lookup"><span data-stu-id="8dd05-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8dd05-105">成員</span><span class="sxs-lookup"><span data-stu-id="8dd05-105">Members</span></span>  
  
|<span data-ttu-id="8dd05-106">member</span><span class="sxs-lookup"><span data-stu-id="8dd05-106">Member</span></span>|<span data-ttu-id="8dd05-107">描述</span><span class="sxs-lookup"><span data-stu-id="8dd05-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="8dd05-108">指示未指定任何關鍵字。</span><span class="sxs-lookup"><span data-stu-id="8dd05-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="8dd05-109">指示指定了 ANSI 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="8dd05-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="8dd05-110">指示指定了 Unicode 關鍵字</span><span class="sxs-lookup"><span data-stu-id="8dd05-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="8dd05-111">指示指定了自動關鍵字。</span><span class="sxs-lookup"><span data-stu-id="8dd05-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="8dd05-112">指示指定了 OLE 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="8dd05-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="8dd05-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="8dd05-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8dd05-114">需求</span><span class="sxs-lookup"><span data-stu-id="8dd05-114">Requirements</span></span>  
 <span data-ttu-id="8dd05-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8dd05-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dd05-116">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="8dd05-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8dd05-117">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="8dd05-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8dd05-118">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dd05-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd05-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dd05-119">See also</span></span>

- [<span data-ttu-id="8dd05-120">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="8dd05-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
