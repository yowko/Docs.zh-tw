---
title: CorCheckDuplicatesFor 列舉
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d04f5589ecffbcde59a6ffbe4f3d6c5f0b1040cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074868"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="76d2d-102">CorCheckDuplicatesFor 列舉</span><span class="sxs-lookup"><span data-stu-id="76d2d-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="76d2d-103">指定要檢查重複項目中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76d2d-104">語法</span><span class="sxs-lookup"><span data-stu-id="76d2d-104">Syntax</span></span>  
  
```  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =   
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |   
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a><span data-ttu-id="76d2d-105">成員</span><span class="sxs-lookup"><span data-stu-id="76d2d-105">Members</span></span>  
  
|<span data-ttu-id="76d2d-106">成員</span><span class="sxs-lookup"><span data-stu-id="76d2d-106">Member</span></span>|<span data-ttu-id="76d2d-107">描述</span><span class="sxs-lookup"><span data-stu-id="76d2d-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="76d2d-108">請檢查重複項目的所有中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="76d2d-109">未使用。</span><span class="sxs-lookup"><span data-stu-id="76d2d-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="76d2d-110">不會檢查重複項目中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="76d2d-111">檢查是否有重複的`mdTypeDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="76d2d-112">檢查是否有重複的`mdInterfaceImpl`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="76d2d-113">檢查是否有重複的`mdMethodDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="76d2d-114">檢查是否有重複的`mdTypeRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="76d2d-115">檢查是否有重複的`mdMemberRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="76d2d-116">檢查是否有重複的`mdCustomAttribute`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="76d2d-117">檢查是否有重複的`mdParamDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="76d2d-118">檢查是否有重複的`mdPermission`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="76d2d-119">檢查是否有重複的`mdProperty`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="76d2d-120">檢查是否有重複的`mdEvent`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="76d2d-121">檢查是否有重複的`mdFieldDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="76d2d-122">檢查是否有重複的`mdSignature`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="76d2d-123">檢查是否有重複的`mdModuleRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="76d2d-124">檢查是否有重複的`mdTypeSpec`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="76d2d-125">檢查是否有重複的`mdImplMap`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="76d2d-126">檢查是否有重複的`mdAssemblyRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="76d2d-127">檢查是否有重複的`mdFile`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="76d2d-128">檢查是否有重複的`mdExportedType`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="76d2d-129">檢查是否有重複的`mdManifestResource`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="76d2d-130">檢查是否有重複的`mdGenericParam`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="76d2d-131">檢查是否有重複的`mdMethodSpec`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="76d2d-132">檢查是否有重複的`mdGenericParamConstraint`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="76d2d-133">檢查是否有重複的`mdAssembly`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="76d2d-134">檢查是否有重複項目`mdMemberRef`， `mdTypeRef`， `mdSignature`， `mdTypeSpec`，和`mdMethodSpec`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76d2d-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="76d2d-135">需求</span><span class="sxs-lookup"><span data-stu-id="76d2d-135">Requirements</span></span>  
 <span data-ttu-id="76d2d-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="76d2d-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76d2d-137">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="76d2d-137">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="76d2d-138">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="76d2d-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="76d2d-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76d2d-139">See also</span></span>

- [<span data-ttu-id="76d2d-140">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="76d2d-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
