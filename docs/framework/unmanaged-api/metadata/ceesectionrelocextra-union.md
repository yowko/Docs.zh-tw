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
ms.openlocfilehash: 9d6a5673c2aaf287131274b0c590f00a69c64fed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517145"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="eeea1-102">CeeSectionRelocExtra 等位</span><span class="sxs-lookup"><span data-stu-id="eeea1-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="eeea1-103">代表可由為位址位移[ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)重新配置區段的介面。</span><span class="sxs-lookup"><span data-stu-id="eeea1-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeea1-104">語法</span><span class="sxs-lookup"><span data-stu-id="eeea1-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="eeea1-105">成員</span><span class="sxs-lookup"><span data-stu-id="eeea1-105">Members</span></span>  
  
|<span data-ttu-id="eeea1-106">成員</span><span class="sxs-lookup"><span data-stu-id="eeea1-106">Member</span></span>|<span data-ttu-id="eeea1-107">描述</span><span class="sxs-lookup"><span data-stu-id="eeea1-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="eeea1-108">區段上方的地址調整。</span><span class="sxs-lookup"><span data-stu-id="eeea1-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eeea1-109">需求</span><span class="sxs-lookup"><span data-stu-id="eeea1-109">Requirements</span></span>  
 <span data-ttu-id="eeea1-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eeea1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eeea1-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eeea1-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eeea1-112">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eeea1-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eeea1-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeea1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeea1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eeea1-114">See also</span></span>
- [<span data-ttu-id="eeea1-115">中繼資料等位</span><span class="sxs-lookup"><span data-stu-id="eeea1-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
