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
ms.openlocfilehash: 8071c3f43775975de37e3255582b6fc8f13f7de3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732777"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="0bf6d-102">ASSEMBLYMETADATA 結構</span><span class="sxs-lookup"><span data-stu-id="0bf6d-102">ASSEMBLYMETADATA Structure</span></span>

<span data-ttu-id="0bf6d-103">包含參考元件的相關資訊，包括其版本，以及其地區設定、處理器和作業系統的支援層級。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bf6d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0bf6d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="0bf6d-105">成員</span><span class="sxs-lookup"><span data-stu-id="0bf6d-105">Members</span></span>  
  
|<span data-ttu-id="0bf6d-106">member</span><span class="sxs-lookup"><span data-stu-id="0bf6d-106">Member</span></span>|<span data-ttu-id="0bf6d-107">描述</span><span class="sxs-lookup"><span data-stu-id="0bf6d-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="0bf6d-108">參考之元件的主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="0bf6d-109">此值不可以是零。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-109">This value cannot be zero.</span></span> <span data-ttu-id="0bf6d-110">如果設定的所有位 `usMajorVersion` ，則不會指定主要版本。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="0bf6d-111">參考之元件的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="0bf6d-112">此值不可以是零。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-112">This value cannot be zero.</span></span> <span data-ttu-id="0bf6d-113">如果設定的所有位 `usMinorVersion` ，則不會指定次要版本。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="0bf6d-114">參考組件的組建編號。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="0bf6d-115">此值不可以是零。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-115">This value cannot be zero.</span></span> <span data-ttu-id="0bf6d-116">如果設定的所有位 `usBuildNumber` ，則不會指定組建編號。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="0bf6d-117">參考元件的修訂編號。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="0bf6d-118">此值不可以是零。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-118">This value cannot be zero.</span></span> <span data-ttu-id="0bf6d-119">如果設定的所有位 `usRevisionNumber` ，則不會指定修訂號碼。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="0bf6d-120">符合 RFC1766 規格的地區設定名稱清單（以分號分隔），指定參考元件所支援的地區設定。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="0bf6d-121">Null 值表示地區設定獨立性。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-121">A null value indicates locale independence.</span></span> <span data-ttu-id="0bf6d-122">**注意：**  在 .NET Framework 1.0 版中，您無法指定一個以上的地區設定。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="0bf6d-123">的大小（以寬字元為單位） `szLocale` 。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="0bf6d-124">定義于 Winnt 中的識別碼陣列，代表受參考元件支援的處理器類型。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="0bf6d-125">Null 值表示處理器獨立性。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="0bf6d-126">`rdwProcessor` 陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="0bf6d-127">[OSINFO](osinfo-structure.md)實例的陣列，指定參考元件所支援的作業系統。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-127">An array of [OSINFO](osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="0bf6d-128">Null 值表示作業系統獨立性。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="0bf6d-129">`rOS` 陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0bf6d-130">需求</span><span class="sxs-lookup"><span data-stu-id="0bf6d-130">Requirements</span></span>  

 <span data-ttu-id="0bf6d-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0bf6d-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bf6d-132">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="0bf6d-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0bf6d-133">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="0bf6d-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0bf6d-134">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bf6d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf6d-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bf6d-135">See also</span></span>

- [<span data-ttu-id="0bf6d-136">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="0bf6d-136">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="0bf6d-137">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="0bf6d-137">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="0bf6d-138">OSINFO 結構</span><span class="sxs-lookup"><span data-stu-id="0bf6d-138">OSINFO Structure</span></span>](osinfo-structure.md)
