---
title: "AssemblyFlags 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyFlags
helpviewer_keywords: AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 91760b6d16b663257bf3d89915da3bd88b3411bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="b4ae0-102">AssemblyFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="b4ae0-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="b4ae0-103">包含描述的組件的執行階段功能的值。</span><span class="sxs-lookup"><span data-stu-id="b4ae0-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4ae0-104">語法</span><span class="sxs-lookup"><span data-stu-id="b4ae0-104">Syntax</span></span>  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b4ae0-105">成員</span><span class="sxs-lookup"><span data-stu-id="b4ae0-105">Members</span></span>  
  
|<span data-ttu-id="b4ae0-106">成員</span><span class="sxs-lookup"><span data-stu-id="b4ae0-106">Member</span></span>|<span data-ttu-id="b4ae0-107">說明</span><span class="sxs-lookup"><span data-stu-id="b4ae0-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="b4ae0-108">指定匯出的類型定義是隱含構成組件檔案中。</span><span class="sxs-lookup"><span data-stu-id="b4ae0-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="b4ae0-109">在.NET framework 1.0 和 1.1 版中，這個值永遠是設定。</span><span class="sxs-lookup"><span data-stu-id="b4ae0-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="b4ae0-110">指定隱含構成組件檔案中定義的資源。</span><span class="sxs-lookup"><span data-stu-id="b4ae0-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="b4ae0-111">在.NET Framework 1.0 和 1.1 中，這個值永遠是設定。</span><span class="sxs-lookup"><span data-stu-id="b4ae0-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="b4ae0-112">指定組件無法執行與其他版本一起執行相同的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="b4ae0-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="b4ae0-113">指定組件無法執行與其他版本一起執行相同的處理序中。</span><span class="sxs-lookup"><span data-stu-id="b4ae0-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="b4ae0-114">指定是否在同一部電腦上執行，無法與其他版本一起執行組件。</span><span class="sxs-lookup"><span data-stu-id="b4ae0-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4ae0-115">備註</span><span class="sxs-lookup"><span data-stu-id="b4ae0-115">Remarks</span></span>  
 <span data-ttu-id="b4ae0-116">0x0070 0x0010 之間的值可用來描述的參考組件-並存相容性功能。</span><span class="sxs-lookup"><span data-stu-id="b4ae0-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="b4ae0-117">如果這些值未設定，組件會假設為-並存相容。</span><span class="sxs-lookup"><span data-stu-id="b4ae0-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4ae0-118">需求</span><span class="sxs-lookup"><span data-stu-id="b4ae0-118">Requirements</span></span>  
 <span data-ttu-id="b4ae0-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4ae0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4ae0-120">**標頭：** MsCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b4ae0-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="b4ae0-121">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b4ae0-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b4ae0-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4ae0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ae0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4ae0-123">See Also</span></span>  
 [<span data-ttu-id="b4ae0-124">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="b4ae0-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="b4ae0-125">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="b4ae0-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
