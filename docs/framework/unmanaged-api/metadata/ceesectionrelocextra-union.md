---
title: CeeSectionRelocExtra 等位
ms.date: 03/30/2017
api_name:
- CeeSectionRelocExtra Union
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocExtra
helpviewer_keywords:
- CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type:
- apiref
ms.openlocfilehash: d11fefe220fdb00457cc48a6cd166673350be049
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006023"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="3e745-102">CeeSectionRelocExtra 等位</span><span class="sxs-lookup"><span data-stu-id="3e745-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="3e745-103">表示[ICeeGen](iceegen-interface.md)介面用來重新放置區段的位址位移。</span><span class="sxs-lookup"><span data-stu-id="3e745-103">Represents an address offset that is used by the [ICeeGen](iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e745-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e745-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="3e745-105">成員</span><span class="sxs-lookup"><span data-stu-id="3e745-105">Members</span></span>  
  
|<span data-ttu-id="3e745-106">成員</span><span class="sxs-lookup"><span data-stu-id="3e745-106">Member</span></span>|<span data-ttu-id="3e745-107">描述</span><span class="sxs-lookup"><span data-stu-id="3e745-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="3e745-108">區段的上方位址調整。</span><span class="sxs-lookup"><span data-stu-id="3e745-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e745-109">需求</span><span class="sxs-lookup"><span data-stu-id="3e745-109">Requirements</span></span>  
 <span data-ttu-id="3e745-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e745-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e745-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3e745-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e745-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3e745-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e745-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e745-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e745-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e745-114">See also</span></span>

- [<span data-ttu-id="3e745-115">中繼資料等位</span><span class="sxs-lookup"><span data-stu-id="3e745-115">Metadata Unions</span></span>](metadata-unions.md)
