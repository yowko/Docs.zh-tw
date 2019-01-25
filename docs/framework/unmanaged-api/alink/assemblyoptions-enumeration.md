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
ms.openlocfilehash: 939e815f4d3adc5f6e1c8b8fc85c9f4b89372501
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571479"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="06d64-102">AssemblyOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="06d64-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="06d64-103">列舉組件的選項。</span><span class="sxs-lookup"><span data-stu-id="06d64-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06d64-104">語法</span><span class="sxs-lookup"><span data-stu-id="06d64-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="06d64-105">欄位</span><span class="sxs-lookup"><span data-stu-id="06d64-105">Fields</span></span>  
  
|<span data-ttu-id="06d64-106">欄位</span><span class="sxs-lookup"><span data-stu-id="06d64-106">Field</span></span>|<span data-ttu-id="06d64-107">描述</span><span class="sxs-lookup"><span data-stu-id="06d64-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="06d64-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="06d64-108">optAssemTitle</span></span>|<span data-ttu-id="06d64-109">字串-表示組件標題。</span><span class="sxs-lookup"><span data-stu-id="06d64-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="06d64-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="06d64-110">optAssemDescription</span></span>|<span data-ttu-id="06d64-111">字串-包含組件描述。</span><span class="sxs-lookup"><span data-stu-id="06d64-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="06d64-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="06d64-112">optAssemConfig</span></span>|<span data-ttu-id="06d64-113">字串-包含組件組態。</span><span class="sxs-lookup"><span data-stu-id="06d64-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="06d64-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="06d64-114">optAssemOS</span></span>|<span data-ttu-id="06d64-115">字串-編碼為:"dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion 」。</span><span class="sxs-lookup"><span data-stu-id="06d64-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="06d64-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="06d64-116">optAssemProcessor</span></span>|<span data-ttu-id="06d64-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="06d64-117">ULONG</span></span>|  
|<span data-ttu-id="06d64-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="06d64-118">optAssemLocale</span></span>|<span data-ttu-id="06d64-119">字串-包含組件的地區設定。</span><span class="sxs-lookup"><span data-stu-id="06d64-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="06d64-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="06d64-120">optAssemVersion</span></span>|<span data-ttu-id="06d64-121">字串-編碼為：「 Major.Minor.Build.Revision。 」</span><span class="sxs-lookup"><span data-stu-id="06d64-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="06d64-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="06d64-122">optAssemCompany</span></span>|<span data-ttu-id="06d64-123">字串-包含公司。</span><span class="sxs-lookup"><span data-stu-id="06d64-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="06d64-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="06d64-124">optAssemProduct</span></span>|<span data-ttu-id="06d64-125">字串-包含產品名稱。</span><span class="sxs-lookup"><span data-stu-id="06d64-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="06d64-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="06d64-126">optAssemProductVersion</span></span>|<span data-ttu-id="06d64-127">字串 (也稱為 InformationalVersion)。</span><span class="sxs-lookup"><span data-stu-id="06d64-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="06d64-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="06d64-128">optAssemCopyright</span></span>|<span data-ttu-id="06d64-129">字串-包含著作權資訊。</span><span class="sxs-lookup"><span data-stu-id="06d64-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="06d64-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="06d64-130">optAssemTrademark</span></span>|<span data-ttu-id="06d64-131">字串-包含商標資訊。</span><span class="sxs-lookup"><span data-stu-id="06d64-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="06d64-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="06d64-132">optAssemKeyFile</span></span>|<span data-ttu-id="06d64-133">字串 （檔案名稱）。</span><span class="sxs-lookup"><span data-stu-id="06d64-133">String (file name).</span></span>|  
|<span data-ttu-id="06d64-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="06d64-134">optAssemKeyName</span></span>|<span data-ttu-id="06d64-135">字串 （索引鍵名稱）。</span><span class="sxs-lookup"><span data-stu-id="06d64-135">String (The key name).</span></span>|  
|<span data-ttu-id="06d64-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="06d64-136">optAssemAlgID</span></span>|<span data-ttu-id="06d64-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="06d64-137">ULONG</span></span>|  
|<span data-ttu-id="06d64-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="06d64-138">optAssemFlags</span></span>|<span data-ttu-id="06d64-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="06d64-139">ULONG</span></span>|  
|<span data-ttu-id="06d64-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="06d64-140">optAssemHalfSign</span></span>|<span data-ttu-id="06d64-141">Bool （也稱為 DelaySign）。</span><span class="sxs-lookup"><span data-stu-id="06d64-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="06d64-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="06d64-142">optAssemFileVersion</span></span>|<span data-ttu-id="06d64-143">字串-編碼為 「 Major.Minor.Build.Revision"-ProductVersion 相同。</span><span class="sxs-lookup"><span data-stu-id="06d64-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="06d64-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="06d64-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="06d64-145">字串-編碼為"Major.Minor.Build.Revision 」。</span><span class="sxs-lookup"><span data-stu-id="06d64-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="06d64-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="06d64-146">optLastAssemOption</span></span>|<span data-ttu-id="06d64-147">元素數目的計數器。</span><span class="sxs-lookup"><span data-stu-id="06d64-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="06d64-148">需求</span><span class="sxs-lookup"><span data-stu-id="06d64-148">Requirements</span></span>  
 <span data-ttu-id="06d64-149">**標頭：** alink.h</span><span class="sxs-lookup"><span data-stu-id="06d64-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="06d64-150">**程式庫**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="06d64-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d64-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06d64-151">See also</span></span>
- [<span data-ttu-id="06d64-152">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="06d64-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
