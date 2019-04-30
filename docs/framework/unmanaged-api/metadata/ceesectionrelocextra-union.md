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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a78a4b82d0b2064c90c938a8614b0c7594f7856
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043286"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="cbcbf-102">CeeSectionRelocExtra 等位</span><span class="sxs-lookup"><span data-stu-id="cbcbf-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="cbcbf-103">代表可由為位址位移[ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)重新配置區段的介面。</span><span class="sxs-lookup"><span data-stu-id="cbcbf-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbcbf-104">語法</span><span class="sxs-lookup"><span data-stu-id="cbcbf-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="cbcbf-105">成員</span><span class="sxs-lookup"><span data-stu-id="cbcbf-105">Members</span></span>  
  
|<span data-ttu-id="cbcbf-106">成員</span><span class="sxs-lookup"><span data-stu-id="cbcbf-106">Member</span></span>|<span data-ttu-id="cbcbf-107">描述</span><span class="sxs-lookup"><span data-stu-id="cbcbf-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="cbcbf-108">區段上方的地址調整。</span><span class="sxs-lookup"><span data-stu-id="cbcbf-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cbcbf-109">需求</span><span class="sxs-lookup"><span data-stu-id="cbcbf-109">Requirements</span></span>  
 <span data-ttu-id="cbcbf-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cbcbf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbcbf-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cbcbf-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cbcbf-112">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cbcbf-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cbcbf-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbcbf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbcbf-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbcbf-114">See also</span></span>

- [<span data-ttu-id="cbcbf-115">中繼資料等位</span><span class="sxs-lookup"><span data-stu-id="cbcbf-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
