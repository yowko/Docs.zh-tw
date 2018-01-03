---
title: "AssemblyOptions 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyOptions
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ad4f9e02ed0d22009fcb8a5ac078231f2cb22e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="c9a44-102">AssemblyOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="c9a44-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="c9a44-103">列舉組件的選項。</span><span class="sxs-lookup"><span data-stu-id="c9a44-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9a44-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9a44-104">Syntax</span></span>  
  
```  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a><span data-ttu-id="c9a44-105">欄位</span><span class="sxs-lookup"><span data-stu-id="c9a44-105">Fields</span></span>  
  
|<span data-ttu-id="c9a44-106">欄位</span><span class="sxs-lookup"><span data-stu-id="c9a44-106">Field</span></span>|<span data-ttu-id="c9a44-107">描述</span><span class="sxs-lookup"><span data-stu-id="c9a44-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9a44-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="c9a44-108">optAssemTitle</span></span>|<span data-ttu-id="c9a44-109">字串-代表組件標題。</span><span class="sxs-lookup"><span data-stu-id="c9a44-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="c9a44-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="c9a44-110">optAssemDescription</span></span>|<span data-ttu-id="c9a44-111">字串-包含組件描述。</span><span class="sxs-lookup"><span data-stu-id="c9a44-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="c9a44-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="c9a44-112">optAssemConfig</span></span>|<span data-ttu-id="c9a44-113">字串-包含組件組態。</span><span class="sxs-lookup"><span data-stu-id="c9a44-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="c9a44-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="c9a44-114">optAssemOS</span></span>|<span data-ttu-id="c9a44-115">字串的編碼為:"dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion"。</span><span class="sxs-lookup"><span data-stu-id="c9a44-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="c9a44-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="c9a44-116">optAssemProcessor</span></span>|<span data-ttu-id="c9a44-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="c9a44-117">ULONG</span></span>|  
|<span data-ttu-id="c9a44-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="c9a44-118">optAssemLocale</span></span>|<span data-ttu-id="c9a44-119">字串-包含組件的地區設定。</span><span class="sxs-lookup"><span data-stu-id="c9a44-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="c9a44-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="c9a44-120">optAssemVersion</span></span>|<span data-ttu-id="c9a44-121">字串的編碼為:"Major.Minor.Build.Revision"。</span><span class="sxs-lookup"><span data-stu-id="c9a44-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="c9a44-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="c9a44-122">optAssemCompany</span></span>|<span data-ttu-id="c9a44-123">字串-包含公司。</span><span class="sxs-lookup"><span data-stu-id="c9a44-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="c9a44-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="c9a44-124">optAssemProduct</span></span>|<span data-ttu-id="c9a44-125">字串-包含產品名稱。</span><span class="sxs-lookup"><span data-stu-id="c9a44-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="c9a44-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="c9a44-126">optAssemProductVersion</span></span>|<span data-ttu-id="c9a44-127">字串 (也稱為 InformationalVersion)。</span><span class="sxs-lookup"><span data-stu-id="c9a44-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="c9a44-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="c9a44-128">optAssemCopyright</span></span>|<span data-ttu-id="c9a44-129">字串-包含著作權資訊。</span><span class="sxs-lookup"><span data-stu-id="c9a44-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="c9a44-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="c9a44-130">optAssemTrademark</span></span>|<span data-ttu-id="c9a44-131">字串-包含商標資訊。</span><span class="sxs-lookup"><span data-stu-id="c9a44-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="c9a44-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="c9a44-132">optAssemKeyFile</span></span>|<span data-ttu-id="c9a44-133">字串 （檔案名稱）。</span><span class="sxs-lookup"><span data-stu-id="c9a44-133">String (file name).</span></span>|  
|<span data-ttu-id="c9a44-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="c9a44-134">optAssemKeyName</span></span>|<span data-ttu-id="c9a44-135">字串 （機碼名稱）。</span><span class="sxs-lookup"><span data-stu-id="c9a44-135">String (The key name).</span></span>|  
|<span data-ttu-id="c9a44-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="c9a44-136">optAssemAlgID</span></span>|<span data-ttu-id="c9a44-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="c9a44-137">ULONG</span></span>|  
|<span data-ttu-id="c9a44-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="c9a44-138">optAssemFlags</span></span>|<span data-ttu-id="c9a44-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="c9a44-139">ULONG</span></span>|  
|<span data-ttu-id="c9a44-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="c9a44-140">optAssemHalfSign</span></span>|<span data-ttu-id="c9a44-141">Bool （也稱為 DelaySign）。</span><span class="sxs-lookup"><span data-stu-id="c9a44-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="c9a44-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="c9a44-142">optAssemFileVersion</span></span>|<span data-ttu-id="c9a44-143">字串的編碼為"Major.Minor.Build.Revision"-ProductVersion 相同。</span><span class="sxs-lookup"><span data-stu-id="c9a44-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="c9a44-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="c9a44-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="c9a44-145">字串的編碼為"Major.Minor.Build.Revision"。</span><span class="sxs-lookup"><span data-stu-id="c9a44-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="c9a44-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="c9a44-146">optLastAssemOption</span></span>|<span data-ttu-id="c9a44-147">元素數目的計數器。</span><span class="sxs-lookup"><span data-stu-id="c9a44-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9a44-148">需求</span><span class="sxs-lookup"><span data-stu-id="c9a44-148">Requirements</span></span>  
 <span data-ttu-id="c9a44-149">**標頭：** alink.h</span><span class="sxs-lookup"><span data-stu-id="c9a44-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="c9a44-150">**程式庫**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="c9a44-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a44-151">請參閱</span><span class="sxs-lookup"><span data-stu-id="c9a44-151">See Also</span></span>  
 [<span data-ttu-id="c9a44-152">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="c9a44-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
