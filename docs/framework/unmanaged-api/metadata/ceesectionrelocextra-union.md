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
ms.openlocfilehash: d5f61aa9b4a65a5f33e64aa4441370c3f7ca5b03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732719"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="b86ab-102">CeeSectionRelocExtra 等位</span><span class="sxs-lookup"><span data-stu-id="b86ab-102">CeeSectionRelocExtra Union</span></span>

<span data-ttu-id="b86ab-103">表示 [ICeeGen](iceegen-interface.md) 介面用來重新放置區段的位址位移。</span><span class="sxs-lookup"><span data-stu-id="b86ab-103">Represents an address offset that is used by the [ICeeGen](iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b86ab-104">語法</span><span class="sxs-lookup"><span data-stu-id="b86ab-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="b86ab-105">成員</span><span class="sxs-lookup"><span data-stu-id="b86ab-105">Members</span></span>  
  
|<span data-ttu-id="b86ab-106">member</span><span class="sxs-lookup"><span data-stu-id="b86ab-106">Member</span></span>|<span data-ttu-id="b86ab-107">描述</span><span class="sxs-lookup"><span data-stu-id="b86ab-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="b86ab-108">區段的上方位址調整。</span><span class="sxs-lookup"><span data-stu-id="b86ab-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b86ab-109">需求</span><span class="sxs-lookup"><span data-stu-id="b86ab-109">Requirements</span></span>  

 <span data-ttu-id="b86ab-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b86ab-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b86ab-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="b86ab-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b86ab-112">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="b86ab-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b86ab-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b86ab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b86ab-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b86ab-114">See also</span></span>

- [<span data-ttu-id="b86ab-115">中繼資料等位</span><span class="sxs-lookup"><span data-stu-id="b86ab-115">Metadata Unions</span></span>](metadata-unions.md)
