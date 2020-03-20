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
ms.openlocfilehash: 048fe687e4d979576896f5310bddc855b40bb695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175222"
---
# <a name="osinfo-structure"></a><span data-ttu-id="23fec-102">OSINFO 結構</span><span class="sxs-lookup"><span data-stu-id="23fec-102">OSINFO Structure</span></span>
<span data-ttu-id="23fec-103">包含有關程式集或模組的作業系統的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="23fec-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23fec-104">語法</span><span class="sxs-lookup"><span data-stu-id="23fec-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="23fec-105">成員</span><span class="sxs-lookup"><span data-stu-id="23fec-105">Members</span></span>  
  
|<span data-ttu-id="23fec-106">member</span><span class="sxs-lookup"><span data-stu-id="23fec-106">Member</span></span>|<span data-ttu-id="23fec-107">描述</span><span class="sxs-lookup"><span data-stu-id="23fec-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="23fec-108">由微軟 Windows 平臺函數`GetVersionEx`定義的識別碼值之一。</span><span class="sxs-lookup"><span data-stu-id="23fec-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="23fec-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="23fec-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="23fec-110">- VER_PLATFORM_WIN32s，或 0x0000，以指定微軟 Windows 3.1。</span><span class="sxs-lookup"><span data-stu-id="23fec-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="23fec-111">- VER_PLATFORM_WIN32_WINDOWS，或 0x0001，以指定 Windows 95、Windows 98 或它們產生的作業系統。</span><span class="sxs-lookup"><span data-stu-id="23fec-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="23fec-112">- VER_PLATFORM_WIN32_NT，或 0x0002，以指定 Windows NT 或作業系統從它下降。</span><span class="sxs-lookup"><span data-stu-id="23fec-112">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="23fec-113">作業系統主版本，或用於指示任何版本的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="23fec-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="23fec-114">作業系統次要版本，或用於指示任何版本的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="23fec-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23fec-115">備註</span><span class="sxs-lookup"><span data-stu-id="23fec-115">Remarks</span></span>  
 <span data-ttu-id="23fec-116">`OSINFO`基於調用微軟`OSVERSIONINFOEX`Windows 平臺功能`GetVersionEx`時使用的結構。</span><span class="sxs-lookup"><span data-stu-id="23fec-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="23fec-117">此結構由 ASSEMBLYMETADATA 結構用於指示其作業系統支援。</span><span class="sxs-lookup"><span data-stu-id="23fec-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23fec-118">需求</span><span class="sxs-lookup"><span data-stu-id="23fec-118">Requirements</span></span>  
 <span data-ttu-id="23fec-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23fec-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23fec-120">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="23fec-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23fec-121">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="23fec-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23fec-122">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23fec-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23fec-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23fec-123">See also</span></span>

- [<span data-ttu-id="23fec-124">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="23fec-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="23fec-125">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="23fec-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
