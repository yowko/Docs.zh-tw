---
title: CorAttributeTargets 列舉
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: fbe721bad56ec2be434039f00e741ad9a177815f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718965"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="73939-102">CorAttributeTargets 列舉</span><span class="sxs-lookup"><span data-stu-id="73939-102">CorAttributeTargets Enumeration</span></span>

<span data-ttu-id="73939-103">指定有效套用屬性的應用程式項目。</span><span class="sxs-lookup"><span data-stu-id="73939-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73939-104">語法</span><span class="sxs-lookup"><span data-stu-id="73939-104">Syntax</span></span>  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =
        catAssembly | catModule | catClass | catStruct |
        catEnum | catConstructor | catMethod | catProperty |
        catField | catEvent | catInterface | catParameter |
        catDelegate | catGenericParameter,  
  
    catClassMembers        =
        catClass | catStruct | catEnum | catConstructor |
        catMethod | catProperty | catField | catEvent |
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a><span data-ttu-id="73939-105">成員</span><span class="sxs-lookup"><span data-stu-id="73939-105">Members</span></span>  
  
|<span data-ttu-id="73939-106">member</span><span class="sxs-lookup"><span data-stu-id="73939-106">Member</span></span>|<span data-ttu-id="73939-107">描述</span><span class="sxs-lookup"><span data-stu-id="73939-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="73939-108">屬性可以套用至組件。</span><span class="sxs-lookup"><span data-stu-id="73939-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="73939-109">屬性可以套用至可攜式可執行檔 ( .dll 或 .exe) 模組。</span><span class="sxs-lookup"><span data-stu-id="73939-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="73939-110">屬性可以套用至類別。</span><span class="sxs-lookup"><span data-stu-id="73939-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="73939-111">屬性可以套用至結構，也就是實值型別 (Value Type)。</span><span class="sxs-lookup"><span data-stu-id="73939-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="73939-112">屬性可以套用至列舉型別。</span><span class="sxs-lookup"><span data-stu-id="73939-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="73939-113">屬性可以套用至建構函式。</span><span class="sxs-lookup"><span data-stu-id="73939-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="73939-114">屬性可以套用至方法。</span><span class="sxs-lookup"><span data-stu-id="73939-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="73939-115">屬性 (Attibute) 可以套用至屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="73939-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="73939-116">屬性可以套用至欄位。</span><span class="sxs-lookup"><span data-stu-id="73939-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="73939-117">屬性可以套用至事件。</span><span class="sxs-lookup"><span data-stu-id="73939-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="73939-118">屬性可以套用至介面。</span><span class="sxs-lookup"><span data-stu-id="73939-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="73939-119">屬性可以套用至參數。</span><span class="sxs-lookup"><span data-stu-id="73939-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="73939-120">屬性可以套用至委派。</span><span class="sxs-lookup"><span data-stu-id="73939-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="73939-121">屬性可以套用至泛型參數。</span><span class="sxs-lookup"><span data-stu-id="73939-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="73939-122">屬性可以套用至任何應用程式項目。</span><span class="sxs-lookup"><span data-stu-id="73939-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="73939-123">屬性可以套用至類別的成員。</span><span class="sxs-lookup"><span data-stu-id="73939-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73939-124">備註</span><span class="sxs-lookup"><span data-stu-id="73939-124">Remarks</span></span>  

 <span data-ttu-id="73939-125">`CorAttributeTargets`列舉值可以與位 or 運算結合，以取得慣用的組合。</span><span class="sxs-lookup"><span data-stu-id="73939-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="73939-126">會將 `CorAttributeTargets` managed <xref:System.AttributeTargets?displayProperty=nameWithType> 列舉平行。</span><span class="sxs-lookup"><span data-stu-id="73939-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73939-127">需求</span><span class="sxs-lookup"><span data-stu-id="73939-127">Requirements</span></span>  

 <span data-ttu-id="73939-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73939-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73939-129">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="73939-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="73939-130">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73939-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73939-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73939-131">See also</span></span>

- [<span data-ttu-id="73939-132">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="73939-132">Metadata Enumerations</span></span>](metadata-enumerations.md)
