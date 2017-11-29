---
title: "CorAttributeTargets 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorAttributeTargets
api_location: mscoree.dll
api_type: COM
f1_keywords: CorAttributeTargets
helpviewer_keywords: CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce783c790eeb15c60d8e7699396755a560df7c9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="ce879-102">CorAttributeTargets 列舉</span><span class="sxs-lookup"><span data-stu-id="ce879-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="ce879-103">指定有效套用屬性的應用程式項目。</span><span class="sxs-lookup"><span data-stu-id="ce879-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce879-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce879-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ce879-105">成員</span><span class="sxs-lookup"><span data-stu-id="ce879-105">Members</span></span>  
  
|<span data-ttu-id="ce879-106">成員</span><span class="sxs-lookup"><span data-stu-id="ce879-106">Member</span></span>|<span data-ttu-id="ce879-107">說明</span><span class="sxs-lookup"><span data-stu-id="ce879-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="ce879-108">屬性可以套用至組件中。</span><span class="sxs-lookup"><span data-stu-id="ce879-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="ce879-109">屬性可以套用至可攜式執行檔 （.dll 或.exe） 模組。</span><span class="sxs-lookup"><span data-stu-id="ce879-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="ce879-110">屬性可以套用至類別。</span><span class="sxs-lookup"><span data-stu-id="ce879-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="ce879-111">屬性可以套用至結構。也就是說，類型的值。</span><span class="sxs-lookup"><span data-stu-id="ce879-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="ce879-112">屬性可以套用至列舉。</span><span class="sxs-lookup"><span data-stu-id="ce879-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="ce879-113">屬性可以套用至建構函式。</span><span class="sxs-lookup"><span data-stu-id="ce879-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="ce879-114">屬性可以套用至方法。</span><span class="sxs-lookup"><span data-stu-id="ce879-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="ce879-115">屬性可以套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="ce879-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="ce879-116">屬性可以套用至欄位。</span><span class="sxs-lookup"><span data-stu-id="ce879-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="ce879-117">屬性可以套用到的事件。</span><span class="sxs-lookup"><span data-stu-id="ce879-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="ce879-118">屬性可以套用至介面。</span><span class="sxs-lookup"><span data-stu-id="ce879-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="ce879-119">屬性可以套用至參數。</span><span class="sxs-lookup"><span data-stu-id="ce879-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="ce879-120">屬性可以套用的委派。</span><span class="sxs-lookup"><span data-stu-id="ce879-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="ce879-121">屬性可以套用至泛型參數。</span><span class="sxs-lookup"><span data-stu-id="ce879-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="ce879-122">屬性可以套用至任何應用程式項目。</span><span class="sxs-lookup"><span data-stu-id="ce879-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="ce879-123">屬性可以套用至類別的成員。</span><span class="sxs-lookup"><span data-stu-id="ce879-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce879-124">備註</span><span class="sxs-lookup"><span data-stu-id="ce879-124">Remarks</span></span>  
 <span data-ttu-id="ce879-125">`CorAttributeTargets`列舉值可以與慣用的組合，將位元 OR 運算結合。</span><span class="sxs-lookup"><span data-stu-id="ce879-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="ce879-126">`CorAttributeTargets`與 managed<xref:System.AttributeTargets?displayProperty=nameWithType>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="ce879-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce879-127">需求</span><span class="sxs-lookup"><span data-stu-id="ce879-127">Requirements</span></span>  
 <span data-ttu-id="ce879-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce879-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce879-129">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ce879-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ce879-130">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce879-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce879-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce879-131">See Also</span></span>  
 [<span data-ttu-id="ce879-132">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="ce879-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
