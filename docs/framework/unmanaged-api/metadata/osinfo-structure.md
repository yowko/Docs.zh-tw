---
title: OSINFO 結構
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: 89111bf7eb03d20c2010c7a20c4cd055c2a021e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430727"
---
# <a name="osinfo-structure"></a><span data-ttu-id="52bc4-102">OSINFO 結構</span><span class="sxs-lookup"><span data-stu-id="52bc4-102">OSINFO Structure</span></span>
<span data-ttu-id="52bc4-103">Contains details about the operating system for an assembly or module.</span><span class="sxs-lookup"><span data-stu-id="52bc4-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52bc4-104">語法</span><span class="sxs-lookup"><span data-stu-id="52bc4-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="52bc4-105">Members</span><span class="sxs-lookup"><span data-stu-id="52bc4-105">Members</span></span>  
  
|<span data-ttu-id="52bc4-106">成員</span><span class="sxs-lookup"><span data-stu-id="52bc4-106">Member</span></span>|<span data-ttu-id="52bc4-107">描述</span><span class="sxs-lookup"><span data-stu-id="52bc4-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="52bc4-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="52bc4-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="52bc4-109">The following values are supported:</span><span class="sxs-lookup"><span data-stu-id="52bc4-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="52bc4-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span><span class="sxs-lookup"><span data-stu-id="52bc4-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="52bc4-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span><span class="sxs-lookup"><span data-stu-id="52bc4-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="52bc4-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span><span class="sxs-lookup"><span data-stu-id="52bc4-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="52bc4-113">The operating system major version, or a NULL value to indicate any version.</span><span class="sxs-lookup"><span data-stu-id="52bc4-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="52bc4-114">The operating system minor version, or a NULL value to indicate any version.</span><span class="sxs-lookup"><span data-stu-id="52bc4-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52bc4-115">備註</span><span class="sxs-lookup"><span data-stu-id="52bc4-115">Remarks</span></span>  
 <span data-ttu-id="52bc4-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="52bc4-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="52bc4-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span><span class="sxs-lookup"><span data-stu-id="52bc4-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52bc4-118">需求</span><span class="sxs-lookup"><span data-stu-id="52bc4-118">Requirements</span></span>  
 <span data-ttu-id="52bc4-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52bc4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52bc4-120">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="52bc4-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52bc4-121">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="52bc4-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52bc4-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52bc4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52bc4-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="52bc4-123">See also</span></span>

- [<span data-ttu-id="52bc4-124">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="52bc4-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="52bc4-125">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="52bc4-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
