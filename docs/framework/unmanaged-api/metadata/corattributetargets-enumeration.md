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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54d239c3091b29424b26fbab4cb4eb9152ff9ad9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442162"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="31479-102">CorAttributeTargets 列舉</span><span class="sxs-lookup"><span data-stu-id="31479-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="31479-103">指定有效套用屬性的應用程式項目。</span><span class="sxs-lookup"><span data-stu-id="31479-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31479-104">語法</span><span class="sxs-lookup"><span data-stu-id="31479-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="31479-105">成員</span><span class="sxs-lookup"><span data-stu-id="31479-105">Members</span></span>  
  
|<span data-ttu-id="31479-106">成員</span><span class="sxs-lookup"><span data-stu-id="31479-106">Member</span></span>|<span data-ttu-id="31479-107">描述</span><span class="sxs-lookup"><span data-stu-id="31479-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="31479-108">屬性可以套用至組件中。</span><span class="sxs-lookup"><span data-stu-id="31479-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="31479-109">屬性可以套用至可攜式執行檔 （.dll 或.exe） 模組。</span><span class="sxs-lookup"><span data-stu-id="31479-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="31479-110">屬性可以套用至類別。</span><span class="sxs-lookup"><span data-stu-id="31479-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="31479-111">屬性可以套用至結構。也就是說，類型的值。</span><span class="sxs-lookup"><span data-stu-id="31479-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="31479-112">屬性可以套用至列舉。</span><span class="sxs-lookup"><span data-stu-id="31479-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="31479-113">屬性可以套用至建構函式。</span><span class="sxs-lookup"><span data-stu-id="31479-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="31479-114">屬性可以套用至方法。</span><span class="sxs-lookup"><span data-stu-id="31479-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="31479-115">屬性可以套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="31479-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="31479-116">屬性可以套用至欄位。</span><span class="sxs-lookup"><span data-stu-id="31479-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="31479-117">屬性可以套用到的事件。</span><span class="sxs-lookup"><span data-stu-id="31479-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="31479-118">屬性可以套用至介面。</span><span class="sxs-lookup"><span data-stu-id="31479-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="31479-119">屬性可以套用至參數。</span><span class="sxs-lookup"><span data-stu-id="31479-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="31479-120">屬性可以套用的委派。</span><span class="sxs-lookup"><span data-stu-id="31479-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="31479-121">屬性可以套用至泛型參數。</span><span class="sxs-lookup"><span data-stu-id="31479-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="31479-122">屬性可以套用至任何應用程式項目。</span><span class="sxs-lookup"><span data-stu-id="31479-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="31479-123">屬性可以套用至類別的成員。</span><span class="sxs-lookup"><span data-stu-id="31479-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31479-124">備註</span><span class="sxs-lookup"><span data-stu-id="31479-124">Remarks</span></span>  
 <span data-ttu-id="31479-125">`CorAttributeTargets`列舉值可以與慣用的組合，將位元 OR 運算結合。</span><span class="sxs-lookup"><span data-stu-id="31479-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="31479-126">`CorAttributeTargets`與 managed<xref:System.AttributeTargets?displayProperty=nameWithType>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="31479-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31479-127">需求</span><span class="sxs-lookup"><span data-stu-id="31479-127">Requirements</span></span>  
 <span data-ttu-id="31479-128">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31479-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31479-129">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="31479-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="31479-130">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31479-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31479-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31479-131">See Also</span></span>  
 [<span data-ttu-id="31479-132">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="31479-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
