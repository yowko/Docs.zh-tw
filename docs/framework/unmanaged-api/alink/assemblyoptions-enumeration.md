---
title: AssemblyOptions 列舉
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3926a0d49b2db02cf52a3cc943b05edc4cc36a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406270"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="01f2d-102">AssemblyOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="01f2d-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="01f2d-103">列舉組件的選項。</span><span class="sxs-lookup"><span data-stu-id="01f2d-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f2d-104">語法</span><span class="sxs-lookup"><span data-stu-id="01f2d-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="01f2d-105">欄位</span><span class="sxs-lookup"><span data-stu-id="01f2d-105">Fields</span></span>  
  
|<span data-ttu-id="01f2d-106">欄位</span><span class="sxs-lookup"><span data-stu-id="01f2d-106">Field</span></span>|<span data-ttu-id="01f2d-107">描述</span><span class="sxs-lookup"><span data-stu-id="01f2d-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="01f2d-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="01f2d-108">optAssemTitle</span></span>|<span data-ttu-id="01f2d-109">字串-代表組件標題。</span><span class="sxs-lookup"><span data-stu-id="01f2d-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="01f2d-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="01f2d-110">optAssemDescription</span></span>|<span data-ttu-id="01f2d-111">字串-包含組件描述。</span><span class="sxs-lookup"><span data-stu-id="01f2d-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="01f2d-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="01f2d-112">optAssemConfig</span></span>|<span data-ttu-id="01f2d-113">字串-包含組件組態。</span><span class="sxs-lookup"><span data-stu-id="01f2d-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="01f2d-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="01f2d-114">optAssemOS</span></span>|<span data-ttu-id="01f2d-115">字串的編碼為:"dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion"。</span><span class="sxs-lookup"><span data-stu-id="01f2d-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="01f2d-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="01f2d-116">optAssemProcessor</span></span>|<span data-ttu-id="01f2d-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="01f2d-117">ULONG</span></span>|  
|<span data-ttu-id="01f2d-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="01f2d-118">optAssemLocale</span></span>|<span data-ttu-id="01f2d-119">字串-包含組件的地區設定。</span><span class="sxs-lookup"><span data-stu-id="01f2d-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="01f2d-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="01f2d-120">optAssemVersion</span></span>|<span data-ttu-id="01f2d-121">字串的編碼為:"Major.Minor.Build.Revision"。</span><span class="sxs-lookup"><span data-stu-id="01f2d-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="01f2d-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="01f2d-122">optAssemCompany</span></span>|<span data-ttu-id="01f2d-123">字串-包含公司。</span><span class="sxs-lookup"><span data-stu-id="01f2d-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="01f2d-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="01f2d-124">optAssemProduct</span></span>|<span data-ttu-id="01f2d-125">字串-包含產品名稱。</span><span class="sxs-lookup"><span data-stu-id="01f2d-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="01f2d-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="01f2d-126">optAssemProductVersion</span></span>|<span data-ttu-id="01f2d-127">字串 (也稱為 InformationalVersion)。</span><span class="sxs-lookup"><span data-stu-id="01f2d-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="01f2d-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="01f2d-128">optAssemCopyright</span></span>|<span data-ttu-id="01f2d-129">字串-包含著作權資訊。</span><span class="sxs-lookup"><span data-stu-id="01f2d-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="01f2d-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="01f2d-130">optAssemTrademark</span></span>|<span data-ttu-id="01f2d-131">字串-包含商標資訊。</span><span class="sxs-lookup"><span data-stu-id="01f2d-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="01f2d-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="01f2d-132">optAssemKeyFile</span></span>|<span data-ttu-id="01f2d-133">字串 （檔案名稱）。</span><span class="sxs-lookup"><span data-stu-id="01f2d-133">String (file name).</span></span>|  
|<span data-ttu-id="01f2d-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="01f2d-134">optAssemKeyName</span></span>|<span data-ttu-id="01f2d-135">字串 （機碼名稱）。</span><span class="sxs-lookup"><span data-stu-id="01f2d-135">String (The key name).</span></span>|  
|<span data-ttu-id="01f2d-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="01f2d-136">optAssemAlgID</span></span>|<span data-ttu-id="01f2d-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="01f2d-137">ULONG</span></span>|  
|<span data-ttu-id="01f2d-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="01f2d-138">optAssemFlags</span></span>|<span data-ttu-id="01f2d-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="01f2d-139">ULONG</span></span>|  
|<span data-ttu-id="01f2d-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="01f2d-140">optAssemHalfSign</span></span>|<span data-ttu-id="01f2d-141">Bool （也稱為 DelaySign）。</span><span class="sxs-lookup"><span data-stu-id="01f2d-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="01f2d-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="01f2d-142">optAssemFileVersion</span></span>|<span data-ttu-id="01f2d-143">字串的編碼為"Major.Minor.Build.Revision"-ProductVersion 相同。</span><span class="sxs-lookup"><span data-stu-id="01f2d-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="01f2d-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="01f2d-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="01f2d-145">字串的編碼為"Major.Minor.Build.Revision"。</span><span class="sxs-lookup"><span data-stu-id="01f2d-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="01f2d-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="01f2d-146">optLastAssemOption</span></span>|<span data-ttu-id="01f2d-147">元素數目的計數器。</span><span class="sxs-lookup"><span data-stu-id="01f2d-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01f2d-148">需求</span><span class="sxs-lookup"><span data-stu-id="01f2d-148">Requirements</span></span>  
 <span data-ttu-id="01f2d-149">**標頭：** alink.h</span><span class="sxs-lookup"><span data-stu-id="01f2d-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="01f2d-150">**程式庫**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="01f2d-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f2d-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01f2d-151">See Also</span></span>  
 [<span data-ttu-id="01f2d-152">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="01f2d-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
