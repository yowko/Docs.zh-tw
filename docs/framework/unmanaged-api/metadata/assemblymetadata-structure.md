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
ms.openlocfilehash: 5c7211fc2523b70313a1e4d4d9d2da0dcecd1d32
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009427"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="1dfac-102">ASSEMBLYMETADATA 結構</span><span class="sxs-lookup"><span data-stu-id="1dfac-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="1dfac-103">包含參考元件的相關資訊，包括其版本，以及其地區設定、處理器和作業系統的支援層級。</span><span class="sxs-lookup"><span data-stu-id="1dfac-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dfac-104">語法</span><span class="sxs-lookup"><span data-stu-id="1dfac-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="1dfac-105">成員</span><span class="sxs-lookup"><span data-stu-id="1dfac-105">Members</span></span>  
  
|<span data-ttu-id="1dfac-106">成員</span><span class="sxs-lookup"><span data-stu-id="1dfac-106">Member</span></span>|<span data-ttu-id="1dfac-107">描述</span><span class="sxs-lookup"><span data-stu-id="1dfac-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="1dfac-108">參考元件的主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="1dfac-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="1dfac-109">這個值不能是零。</span><span class="sxs-lookup"><span data-stu-id="1dfac-109">This value cannot be zero.</span></span> <span data-ttu-id="1dfac-110">如果所有的位 `usMajorVersion` 都已設定，則不會指定主要版本。</span><span class="sxs-lookup"><span data-stu-id="1dfac-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="1dfac-111">參考元件的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="1dfac-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="1dfac-112">這個值不能是零。</span><span class="sxs-lookup"><span data-stu-id="1dfac-112">This value cannot be zero.</span></span> <span data-ttu-id="1dfac-113">如果設定了的所有位 `usMinorVersion` ，則不會指定次要版本。</span><span class="sxs-lookup"><span data-stu-id="1dfac-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="1dfac-114">參考組件的組建編號。</span><span class="sxs-lookup"><span data-stu-id="1dfac-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="1dfac-115">這個值不能是零。</span><span class="sxs-lookup"><span data-stu-id="1dfac-115">This value cannot be zero.</span></span> <span data-ttu-id="1dfac-116">如果設定了的所有位 `usBuildNumber` ，則不會指定組建編號。</span><span class="sxs-lookup"><span data-stu-id="1dfac-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="1dfac-117">參考元件的修訂編號。</span><span class="sxs-lookup"><span data-stu-id="1dfac-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="1dfac-118">這個值不能是零。</span><span class="sxs-lookup"><span data-stu-id="1dfac-118">This value cannot be zero.</span></span> <span data-ttu-id="1dfac-119">如果設定了的所有位 `usRevisionNumber` ，則不會指定修訂編號。</span><span class="sxs-lookup"><span data-stu-id="1dfac-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="1dfac-120">符合 RFC1766 規格的地區設定名稱清單（以分號分隔），指定參考元件所支援的地區設定。</span><span class="sxs-lookup"><span data-stu-id="1dfac-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="1dfac-121">Null 值表示地區設定獨立性。</span><span class="sxs-lookup"><span data-stu-id="1dfac-121">A null value indicates locale independence.</span></span> <span data-ttu-id="1dfac-122">**注意：** 在 .NET Framework 版本1.0 中，您不能指定多個地區設定。</span><span class="sxs-lookup"><span data-stu-id="1dfac-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="1dfac-123">的大小（以寬字元為單位） `szLocale` 。</span><span class="sxs-lookup"><span data-stu-id="1dfac-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="1dfac-124">如 Winnt 中所定義的識別碼陣列，適用于所參考元件所支援的處理器類型。</span><span class="sxs-lookup"><span data-stu-id="1dfac-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="1dfac-125">Null 值表示處理器獨立性。</span><span class="sxs-lookup"><span data-stu-id="1dfac-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="1dfac-126">`rdwProcessor` 陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="1dfac-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="1dfac-127">[OSINFO](osinfo-structure.md)實例的陣列，指定受參考元件支援的作業系統。</span><span class="sxs-lookup"><span data-stu-id="1dfac-127">An array of [OSINFO](osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="1dfac-128">Null 值表示作業系統獨立性。</span><span class="sxs-lookup"><span data-stu-id="1dfac-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="1dfac-129">`rOS` 陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="1dfac-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1dfac-130">需求</span><span class="sxs-lookup"><span data-stu-id="1dfac-130">Requirements</span></span>  
 <span data-ttu-id="1dfac-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1dfac-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dfac-132">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="1dfac-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1dfac-133">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="1dfac-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1dfac-134">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dfac-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dfac-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dfac-135">See also</span></span>

- [<span data-ttu-id="1dfac-136">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="1dfac-136">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="1dfac-137">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1dfac-137">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="1dfac-138">OSINFO 結構</span><span class="sxs-lookup"><span data-stu-id="1dfac-138">OSINFO Structure</span></span>](osinfo-structure.md)
