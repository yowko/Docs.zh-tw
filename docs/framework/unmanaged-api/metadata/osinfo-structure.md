---
title: "OSINFO 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd30fe7904fa6c0685dd9c39931cc545e4e30583
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="osinfo-structure"></a><span data-ttu-id="0e18f-102">OSINFO 結構</span><span class="sxs-lookup"><span data-stu-id="0e18f-102">OSINFO Structure</span></span>
<span data-ttu-id="0e18f-103">包含有關組件或模組的作業系統的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0e18f-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e18f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e18f-104">Syntax</span></span>  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="0e18f-105">成員</span><span class="sxs-lookup"><span data-stu-id="0e18f-105">Members</span></span>  
  
|<span data-ttu-id="0e18f-106">成員</span><span class="sxs-lookup"><span data-stu-id="0e18f-106">Member</span></span>|<span data-ttu-id="0e18f-107">描述</span><span class="sxs-lookup"><span data-stu-id="0e18f-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="0e18f-108">Microsoft Windows 平台函數所定義的識別碼值的其中一個`GetVersionEx`。</span><span class="sxs-lookup"><span data-stu-id="0e18f-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="0e18f-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="0e18f-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="0e18f-110">-VER_PLATFORM_WIN32s 或 0x0000，指定 Microsoft Windows 3.1。</span><span class="sxs-lookup"><span data-stu-id="0e18f-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="0e18f-111">-VER_PLATFORM_WIN32_WINDOWS，或者 0x0001，指定 Windows 95、 Windows 98、 或從它們繼承而來的作業系統。</span><span class="sxs-lookup"><span data-stu-id="0e18f-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="0e18f-112">-VER_PLATFORM_WIN32_NT，或者 0x0010，指定 Windows NT 或從它繼承而來的作業系統。</span><span class="sxs-lookup"><span data-stu-id="0e18f-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="0e18f-113">作業系統主要版本或 NULL 值，指出任何版本。</span><span class="sxs-lookup"><span data-stu-id="0e18f-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="0e18f-114">作業系統次要版本或 NULL 值，指出任何版本。</span><span class="sxs-lookup"><span data-stu-id="0e18f-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e18f-115">備註</span><span class="sxs-lookup"><span data-stu-id="0e18f-115">Remarks</span></span>  
 <span data-ttu-id="0e18f-116">`OSINFO`根據`OSVERSIONINFOEX`結構中使用的 Microsoft Windows 平台函式呼叫`GetVersionEx`。</span><span class="sxs-lookup"><span data-stu-id="0e18f-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="0e18f-117">此結構供 ASSEMBLYMETADATA 結構中，以指出其作業系統支援。</span><span class="sxs-lookup"><span data-stu-id="0e18f-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e18f-118">需求</span><span class="sxs-lookup"><span data-stu-id="0e18f-118">Requirements</span></span>  
 <span data-ttu-id="0e18f-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e18f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e18f-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0e18f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e18f-121">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0e18f-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e18f-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e18f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e18f-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="0e18f-123">See Also</span></span>  
 [<span data-ttu-id="0e18f-124">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="0e18f-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="0e18f-125">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="0e18f-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
