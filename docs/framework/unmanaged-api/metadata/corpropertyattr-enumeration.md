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
ms.openlocfilehash: d76de80f87a8e5a63eac9f6a413f2efb0e394b0a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706121"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="11b4e-102">CorPropertyAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="11b4e-102">CorPropertyAttr Enumeration</span></span>

<span data-ttu-id="11b4e-103">包含值，這些值描述屬性的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="11b4e-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11b4e-104">語法</span><span class="sxs-lookup"><span data-stu-id="11b4e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="11b4e-105">成員</span><span class="sxs-lookup"><span data-stu-id="11b4e-105">Members</span></span>  
  
|<span data-ttu-id="11b4e-106">member</span><span class="sxs-lookup"><span data-stu-id="11b4e-106">Member</span></span>|<span data-ttu-id="11b4e-107">描述</span><span class="sxs-lookup"><span data-stu-id="11b4e-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="11b4e-108">指定屬性是特殊的，且其名稱會描述如何。</span><span class="sxs-lookup"><span data-stu-id="11b4e-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="11b4e-109">保留給 common language runtime 內部使用。</span><span class="sxs-lookup"><span data-stu-id="11b4e-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="11b4e-110">指定 common language runtime 中繼資料內部 Api 應該檢查屬性名稱的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="11b4e-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="11b4e-111">指定屬性具有預設值。</span><span class="sxs-lookup"><span data-stu-id="11b4e-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="11b4e-112">未使用的。</span><span class="sxs-lookup"><span data-stu-id="11b4e-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="11b4e-113">需求</span><span class="sxs-lookup"><span data-stu-id="11b4e-113">Requirements</span></span>  

 <span data-ttu-id="11b4e-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11b4e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11b4e-115">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="11b4e-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="11b4e-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11b4e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11b4e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11b4e-117">See also</span></span>

- [<span data-ttu-id="11b4e-118">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="11b4e-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
