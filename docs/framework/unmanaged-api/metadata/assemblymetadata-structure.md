---
title: ASSEMBLYMETADATA 結構
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83f6190872ecf4435688f3b7c82a61f5f15d9f62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443322"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="06925-102">ASSEMBLYMETADATA 結構</span><span class="sxs-lookup"><span data-stu-id="06925-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="06925-103">包含參考的組件，包括其版本和層級支援地區設定、 處理器和作業系統的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="06925-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06925-104">語法</span><span class="sxs-lookup"><span data-stu-id="06925-104">Syntax</span></span>  
  
```  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a><span data-ttu-id="06925-105">成員</span><span class="sxs-lookup"><span data-stu-id="06925-105">Members</span></span>  
  
|<span data-ttu-id="06925-106">成員</span><span class="sxs-lookup"><span data-stu-id="06925-106">Member</span></span>|<span data-ttu-id="06925-107">描述</span><span class="sxs-lookup"><span data-stu-id="06925-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="06925-108">參考的組件的主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="06925-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="06925-109">此值不可為零。</span><span class="sxs-lookup"><span data-stu-id="06925-109">This value cannot be zero.</span></span> <span data-ttu-id="06925-110">如果所有的位元`usMajorVersion`設定，未指定的主要版本。</span><span class="sxs-lookup"><span data-stu-id="06925-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="06925-111">參考的組件的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="06925-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="06925-112">此值不可為零。</span><span class="sxs-lookup"><span data-stu-id="06925-112">This value cannot be zero.</span></span> <span data-ttu-id="06925-113">如果所有的位元`usMinorVersion`設定，未指定的次要版本。</span><span class="sxs-lookup"><span data-stu-id="06925-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="06925-114">參考的組件的組建編號。</span><span class="sxs-lookup"><span data-stu-id="06925-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="06925-115">此值不可為零。</span><span class="sxs-lookup"><span data-stu-id="06925-115">This value cannot be zero.</span></span> <span data-ttu-id="06925-116">如果所有的位元`usBuildNumber`設定，未指定組建編號。</span><span class="sxs-lookup"><span data-stu-id="06925-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="06925-117">參考的組件的修訂編號。</span><span class="sxs-lookup"><span data-stu-id="06925-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="06925-118">此值不可為零。</span><span class="sxs-lookup"><span data-stu-id="06925-118">This value cannot be zero.</span></span> <span data-ttu-id="06925-119">如果所有的位元`usRevisionNumber`設定，未指定版本號碼。</span><span class="sxs-lookup"><span data-stu-id="06925-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="06925-120">符合 RFC1766 規格中，以分號分隔，指定參考的組件所支援的地區設定的地區設定名稱清單。</span><span class="sxs-lookup"><span data-stu-id="06925-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="06925-121">Null 值表示地區設定的獨立性。</span><span class="sxs-lookup"><span data-stu-id="06925-121">A null value indicates locale independence.</span></span> <span data-ttu-id="06925-122">**注意：** .NET Framework 版本 1.0，您無法指定多個地區設定中。</span><span class="sxs-lookup"><span data-stu-id="06925-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="06925-123">中的寬字元大小`szLocale`。</span><span class="sxs-lookup"><span data-stu-id="06925-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="06925-124">陣列的識別項，在 Winnt.h 中定義的類型所參考的組件支援的處理器。</span><span class="sxs-lookup"><span data-stu-id="06925-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="06925-125">NULL 值，表示處理器獨立性。</span><span class="sxs-lookup"><span data-stu-id="06925-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="06925-126">長度`rdwProcessor`陣列。</span><span class="sxs-lookup"><span data-stu-id="06925-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="06925-127">陣列[OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)指定參考的組件所支援之作業系統的執行個體。</span><span class="sxs-lookup"><span data-stu-id="06925-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="06925-128">NULL 值表示作業系統獨立性。</span><span class="sxs-lookup"><span data-stu-id="06925-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="06925-129">長度`rOS`陣列。</span><span class="sxs-lookup"><span data-stu-id="06925-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="06925-130">需求</span><span class="sxs-lookup"><span data-stu-id="06925-130">Requirements</span></span>  
 <span data-ttu-id="06925-131">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06925-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06925-132">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="06925-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="06925-133">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="06925-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="06925-134">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06925-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06925-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06925-135">See Also</span></span>  
 [<span data-ttu-id="06925-136">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="06925-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="06925-137">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="06925-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="06925-138">OSINFO 結構</span><span class="sxs-lookup"><span data-stu-id="06925-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
