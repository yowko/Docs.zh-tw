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
ms.openlocfilehash: c2e73caa3c69090bca30c8d4a907ddb619bd0ed4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776330"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="d4df2-102">CeeSectionRelocExtra 等位</span><span class="sxs-lookup"><span data-stu-id="d4df2-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="d4df2-103">代表可由為位址位移[ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)重新配置區段的介面。</span><span class="sxs-lookup"><span data-stu-id="d4df2-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4df2-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4df2-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="d4df2-105">成員</span><span class="sxs-lookup"><span data-stu-id="d4df2-105">Members</span></span>  
  
|<span data-ttu-id="d4df2-106">成員</span><span class="sxs-lookup"><span data-stu-id="d4df2-106">Member</span></span>|<span data-ttu-id="d4df2-107">描述</span><span class="sxs-lookup"><span data-stu-id="d4df2-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="d4df2-108">區段上方的地址調整。</span><span class="sxs-lookup"><span data-stu-id="d4df2-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d4df2-109">需求</span><span class="sxs-lookup"><span data-stu-id="d4df2-109">Requirements</span></span>  
 <span data-ttu-id="d4df2-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4df2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4df2-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d4df2-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4df2-112">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d4df2-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4df2-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4df2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4df2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4df2-114">See also</span></span>

- [<span data-ttu-id="d4df2-115">中繼資料等位</span><span class="sxs-lookup"><span data-stu-id="d4df2-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
