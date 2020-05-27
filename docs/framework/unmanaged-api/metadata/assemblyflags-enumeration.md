---
title: AssemblyFlags 列舉
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
ms.openlocfilehash: 1cb84b94b37a2e9e8dd4d20d09cbca82db290c0f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009443"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="f8136-102">AssemblyFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="f8136-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="f8136-103">包含描述元件執行時間功能的值。</span><span class="sxs-lookup"><span data-stu-id="f8136-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8136-104">語法</span><span class="sxs-lookup"><span data-stu-id="f8136-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f8136-105">成員</span><span class="sxs-lookup"><span data-stu-id="f8136-105">Members</span></span>  
  
|<span data-ttu-id="f8136-106">成員</span><span class="sxs-lookup"><span data-stu-id="f8136-106">Member</span></span>|<span data-ttu-id="f8136-107">描述</span><span class="sxs-lookup"><span data-stu-id="f8136-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="f8136-108">指定匯出的類型定義在組成元件的檔案中是隱含的。</span><span class="sxs-lookup"><span data-stu-id="f8136-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="f8136-109">在 .NET Framework 版本1.0 和1.1 中，一律假設已設定此值。</span><span class="sxs-lookup"><span data-stu-id="f8136-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="f8136-110">指定資源定義在組成元件的檔案中是隱含的。</span><span class="sxs-lookup"><span data-stu-id="f8136-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="f8136-111">在 .NET Framework 1.0 和1.1 中，一律假設已設定此值。</span><span class="sxs-lookup"><span data-stu-id="f8136-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="f8136-112">指定如果元件在相同的應用程式域中執行，則無法與其他版本一起執行。</span><span class="sxs-lookup"><span data-stu-id="f8136-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="f8136-113">指定如果元件在相同的進程中執行，則無法與其他版本一起執行。</span><span class="sxs-lookup"><span data-stu-id="f8136-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="f8136-114">指定如果元件在同一部電腦上執行，則無法與其他版本一起執行。</span><span class="sxs-lookup"><span data-stu-id="f8136-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8136-115">備註</span><span class="sxs-lookup"><span data-stu-id="f8136-115">Remarks</span></span>  
 <span data-ttu-id="f8136-116">0x0010 和0x0070 之間的值（含）是用來描述所參考元件的並存相容性功能。</span><span class="sxs-lookup"><span data-stu-id="f8136-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="f8136-117">如果未設定這些值，則會假設元件與並存相容。</span><span class="sxs-lookup"><span data-stu-id="f8136-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8136-118">需求</span><span class="sxs-lookup"><span data-stu-id="f8136-118">Requirements</span></span>  
 <span data-ttu-id="f8136-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8136-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8136-120">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="f8136-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="f8136-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f8136-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8136-122">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8136-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8136-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8136-123">See also</span></span>

- [<span data-ttu-id="f8136-124">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="f8136-124">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="f8136-125">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="f8136-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
