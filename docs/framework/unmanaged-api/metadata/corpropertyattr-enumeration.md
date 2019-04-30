---
title: CorPropertyAttr 列舉
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f1a0fff266e964b506b2dc7c4030caa54abaa5ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045366"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="256bc-102">CorPropertyAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="256bc-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="256bc-103">包含值，這些值描述屬性的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="256bc-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="256bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="256bc-104">Syntax</span></span>  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="256bc-105">成員</span><span class="sxs-lookup"><span data-stu-id="256bc-105">Members</span></span>  
  
|<span data-ttu-id="256bc-106">成員</span><span class="sxs-lookup"><span data-stu-id="256bc-106">Member</span></span>|<span data-ttu-id="256bc-107">描述</span><span class="sxs-lookup"><span data-stu-id="256bc-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="256bc-108">指定屬性是特殊的且其名稱描述方式。</span><span class="sxs-lookup"><span data-stu-id="256bc-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="256bc-109">保留供內部使用的 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="256bc-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="256bc-110">指定 common language runtime 中繼資料內部 Api 應該檢查屬性名稱的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="256bc-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="256bc-111">指定屬性具有預設值。</span><span class="sxs-lookup"><span data-stu-id="256bc-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="256bc-112">未使用。</span><span class="sxs-lookup"><span data-stu-id="256bc-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="256bc-113">需求</span><span class="sxs-lookup"><span data-stu-id="256bc-113">Requirements</span></span>  
 <span data-ttu-id="256bc-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="256bc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="256bc-115">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="256bc-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="256bc-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="256bc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="256bc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="256bc-117">See also</span></span>

- [<span data-ttu-id="256bc-118">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="256bc-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
