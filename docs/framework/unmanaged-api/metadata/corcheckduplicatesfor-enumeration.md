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
ms.openlocfilehash: 04dc12ab4d7d178ebf1575a3260f9f4981972782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176184"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="345e7-102">CorCheckDuplicatesFor 列舉</span><span class="sxs-lookup"><span data-stu-id="345e7-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="345e7-103">指定將檢查重複項的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="345e7-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="345e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="345e7-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="345e7-105">成員</span><span class="sxs-lookup"><span data-stu-id="345e7-105">Members</span></span>  
  
|<span data-ttu-id="345e7-106">member</span><span class="sxs-lookup"><span data-stu-id="345e7-106">Member</span></span>|<span data-ttu-id="345e7-107">描述</span><span class="sxs-lookup"><span data-stu-id="345e7-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="345e7-108">檢查所有中繼資料權杖的重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="345e7-109">未使用。</span><span class="sxs-lookup"><span data-stu-id="345e7-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="345e7-110">不要檢查中繼資料權杖的重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="345e7-111">檢查權杖的`mdTypeDef`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="345e7-112">檢查權杖的`mdInterfaceImpl`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="345e7-113">檢查權杖的`mdMethodDef`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="345e7-114">檢查權杖的`mdTypeRef`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="345e7-115">檢查權杖的`mdMemberRef`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="345e7-116">檢查權杖的`mdCustomAttribute`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="345e7-117">檢查權杖的`mdParamDef`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="345e7-118">檢查權杖的`mdPermission`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="345e7-119">檢查權杖的`mdProperty`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="345e7-120">檢查權杖的`mdEvent`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="345e7-121">檢查權杖的`mdFieldDef`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="345e7-122">檢查權杖的`mdSignature`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="345e7-123">檢查權杖的`mdModuleRef`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="345e7-124">檢查權杖的`mdTypeSpec`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="345e7-125">檢查權杖的`mdImplMap`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="345e7-126">檢查權杖的`mdAssemblyRef`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="345e7-127">檢查權杖的`mdFile`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="345e7-128">檢查權杖的`mdExportedType`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="345e7-129">檢查權杖的`mdManifestResource`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="345e7-130">檢查權杖的`mdGenericParam`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="345e7-131">檢查權杖的`mdMethodSpec`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="345e7-132">檢查權杖的`mdGenericParamConstraint`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="345e7-133">檢查權杖的`mdAssembly`重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="345e7-134">檢查`mdMemberRef`、、、`mdTypeRef``mdSignature``mdTypeSpec`和`mdMethodSpec`權杖的重複項。</span><span class="sxs-lookup"><span data-stu-id="345e7-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="345e7-135">需求</span><span class="sxs-lookup"><span data-stu-id="345e7-135">Requirements</span></span>  
 <span data-ttu-id="345e7-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="345e7-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="345e7-137">**標題：** 科爾赫德</span><span class="sxs-lookup"><span data-stu-id="345e7-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="345e7-138">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="345e7-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="345e7-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="345e7-139">See also</span></span>

- [<span data-ttu-id="345e7-140">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="345e7-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
