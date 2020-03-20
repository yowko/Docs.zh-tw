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
ms.openlocfilehash: 51741aa3a6d965c1e9743081628d8ad62e8fb04e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176197"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="e171c-102">CorAttributeTargets 列舉</span><span class="sxs-lookup"><span data-stu-id="e171c-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="e171c-103">指定有效套用屬性的應用程式項目。</span><span class="sxs-lookup"><span data-stu-id="e171c-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e171c-104">語法</span><span class="sxs-lookup"><span data-stu-id="e171c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="e171c-105">成員</span><span class="sxs-lookup"><span data-stu-id="e171c-105">Members</span></span>  
  
|<span data-ttu-id="e171c-106">member</span><span class="sxs-lookup"><span data-stu-id="e171c-106">Member</span></span>|<span data-ttu-id="e171c-107">描述</span><span class="sxs-lookup"><span data-stu-id="e171c-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="e171c-108">屬性可以套用至組件。</span><span class="sxs-lookup"><span data-stu-id="e171c-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="e171c-109">屬性可以應用於可移植可執行 （.dll 或 .exe） 模組。</span><span class="sxs-lookup"><span data-stu-id="e171c-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="e171c-110">屬性可以套用至類別。</span><span class="sxs-lookup"><span data-stu-id="e171c-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="e171c-111">屬性可以套用至結構，也就是實值型別 (Value Type)。</span><span class="sxs-lookup"><span data-stu-id="e171c-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="e171c-112">屬性可以套用至列舉型別。</span><span class="sxs-lookup"><span data-stu-id="e171c-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="e171c-113">屬性可以套用至建構函式。</span><span class="sxs-lookup"><span data-stu-id="e171c-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="e171c-114">屬性可以套用至方法。</span><span class="sxs-lookup"><span data-stu-id="e171c-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="e171c-115">屬性 (Attibute) 可以套用至屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="e171c-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="e171c-116">屬性可以套用至欄位。</span><span class="sxs-lookup"><span data-stu-id="e171c-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="e171c-117">屬性可以套用至事件。</span><span class="sxs-lookup"><span data-stu-id="e171c-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="e171c-118">屬性可以套用至介面。</span><span class="sxs-lookup"><span data-stu-id="e171c-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="e171c-119">屬性可以套用至參數。</span><span class="sxs-lookup"><span data-stu-id="e171c-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="e171c-120">屬性可以套用至委派。</span><span class="sxs-lookup"><span data-stu-id="e171c-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="e171c-121">屬性可以套用至泛型參數。</span><span class="sxs-lookup"><span data-stu-id="e171c-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="e171c-122">屬性可以套用至任何應用程式項目。</span><span class="sxs-lookup"><span data-stu-id="e171c-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="e171c-123">屬性可以應用於類的成員。</span><span class="sxs-lookup"><span data-stu-id="e171c-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e171c-124">備註</span><span class="sxs-lookup"><span data-stu-id="e171c-124">Remarks</span></span>  
 <span data-ttu-id="e171c-125">枚`CorAttributeTargets`舉值可以與位或操作組合，以獲得首選組合。</span><span class="sxs-lookup"><span data-stu-id="e171c-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="e171c-126">並行`CorAttributeTargets`化託管<xref:System.AttributeTargets?displayProperty=nameWithType>枚舉。</span><span class="sxs-lookup"><span data-stu-id="e171c-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e171c-127">需求</span><span class="sxs-lookup"><span data-stu-id="e171c-127">Requirements</span></span>  
 <span data-ttu-id="e171c-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e171c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e171c-129">**標題：** 科爾赫德</span><span class="sxs-lookup"><span data-stu-id="e171c-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e171c-130">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e171c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e171c-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e171c-131">See also</span></span>

- [<span data-ttu-id="e171c-132">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="e171c-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
