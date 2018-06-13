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
ms.openlocfilehash: c7634ec801a30aa7ba07954c1df0c3d37ec279eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440297"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="bd469-102">CeeSectionRelocExtra 等位</span><span class="sxs-lookup"><span data-stu-id="bd469-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="bd469-103">表示所使用的位址位移[ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)介面來重新配置區段。</span><span class="sxs-lookup"><span data-stu-id="bd469-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd469-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd469-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="bd469-105">成員</span><span class="sxs-lookup"><span data-stu-id="bd469-105">Members</span></span>  
  
|<span data-ttu-id="bd469-106">成員</span><span class="sxs-lookup"><span data-stu-id="bd469-106">Member</span></span>|<span data-ttu-id="bd469-107">描述</span><span class="sxs-lookup"><span data-stu-id="bd469-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="bd469-108">區段上限位址調整。</span><span class="sxs-lookup"><span data-stu-id="bd469-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bd469-109">需求</span><span class="sxs-lookup"><span data-stu-id="bd469-109">Requirements</span></span>  
 <span data-ttu-id="bd469-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd469-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd469-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bd469-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd469-112">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bd469-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd469-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd469-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd469-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd469-114">See Also</span></span>  
 [<span data-ttu-id="bd469-115">中繼資料等位</span><span class="sxs-lookup"><span data-stu-id="bd469-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
