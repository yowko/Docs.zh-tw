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
ms.openlocfilehash: 324e30f6cbcaa1d1d81c7c03967dbb629d2cd6e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742274"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="45851-102">AssemblyOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="45851-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="45851-103">列舉組件的選項。</span><span class="sxs-lookup"><span data-stu-id="45851-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45851-104">語法</span><span class="sxs-lookup"><span data-stu-id="45851-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="fields"></a><span data-ttu-id="45851-105">欄位</span><span class="sxs-lookup"><span data-stu-id="45851-105">Fields</span></span>  
  
|<span data-ttu-id="45851-106">欄位</span><span class="sxs-lookup"><span data-stu-id="45851-106">Field</span></span>|<span data-ttu-id="45851-107">說明</span><span class="sxs-lookup"><span data-stu-id="45851-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="45851-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="45851-108">optAssemTitle</span></span>|<span data-ttu-id="45851-109">字串-表示組件標題。</span><span class="sxs-lookup"><span data-stu-id="45851-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="45851-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="45851-110">optAssemDescription</span></span>|<span data-ttu-id="45851-111">字串-包含組件描述。</span><span class="sxs-lookup"><span data-stu-id="45851-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="45851-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="45851-112">optAssemConfig</span></span>|<span data-ttu-id="45851-113">字串-包含組件組態。</span><span class="sxs-lookup"><span data-stu-id="45851-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="45851-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="45851-114">optAssemOS</span></span>|<span data-ttu-id="45851-115">字串-編碼為:"dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion 」。</span><span class="sxs-lookup"><span data-stu-id="45851-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="45851-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="45851-116">optAssemProcessor</span></span>|<span data-ttu-id="45851-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="45851-117">ULONG</span></span>|  
|<span data-ttu-id="45851-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="45851-118">optAssemLocale</span></span>|<span data-ttu-id="45851-119">字串-包含組件的地區設定。</span><span class="sxs-lookup"><span data-stu-id="45851-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="45851-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="45851-120">optAssemVersion</span></span>|<span data-ttu-id="45851-121">字串-編碼為：「 Major.Minor.Build.Revision。 」</span><span class="sxs-lookup"><span data-stu-id="45851-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="45851-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="45851-122">optAssemCompany</span></span>|<span data-ttu-id="45851-123">字串-包含公司。</span><span class="sxs-lookup"><span data-stu-id="45851-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="45851-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="45851-124">optAssemProduct</span></span>|<span data-ttu-id="45851-125">字串-包含產品名稱。</span><span class="sxs-lookup"><span data-stu-id="45851-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="45851-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="45851-126">optAssemProductVersion</span></span>|<span data-ttu-id="45851-127">字串 (也稱為 InformationalVersion)。</span><span class="sxs-lookup"><span data-stu-id="45851-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="45851-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="45851-128">optAssemCopyright</span></span>|<span data-ttu-id="45851-129">字串-包含著作權資訊。</span><span class="sxs-lookup"><span data-stu-id="45851-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="45851-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="45851-130">optAssemTrademark</span></span>|<span data-ttu-id="45851-131">字串-包含商標資訊。</span><span class="sxs-lookup"><span data-stu-id="45851-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="45851-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="45851-132">optAssemKeyFile</span></span>|<span data-ttu-id="45851-133">字串 （檔案名稱）。</span><span class="sxs-lookup"><span data-stu-id="45851-133">String (file name).</span></span>|  
|<span data-ttu-id="45851-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="45851-134">optAssemKeyName</span></span>|<span data-ttu-id="45851-135">字串 （索引鍵名稱）。</span><span class="sxs-lookup"><span data-stu-id="45851-135">String (The key name).</span></span>|  
|<span data-ttu-id="45851-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="45851-136">optAssemAlgID</span></span>|<span data-ttu-id="45851-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="45851-137">ULONG</span></span>|  
|<span data-ttu-id="45851-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="45851-138">optAssemFlags</span></span>|<span data-ttu-id="45851-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="45851-139">ULONG</span></span>|  
|<span data-ttu-id="45851-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="45851-140">optAssemHalfSign</span></span>|<span data-ttu-id="45851-141">Bool （也稱為 DelaySign）。</span><span class="sxs-lookup"><span data-stu-id="45851-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="45851-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="45851-142">optAssemFileVersion</span></span>|<span data-ttu-id="45851-143">字串-編碼為 「 Major.Minor.Build.Revision"-ProductVersion 相同。</span><span class="sxs-lookup"><span data-stu-id="45851-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="45851-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="45851-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="45851-145">字串-編碼為"Major.Minor.Build.Revision 」。</span><span class="sxs-lookup"><span data-stu-id="45851-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="45851-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="45851-146">optLastAssemOption</span></span>|<span data-ttu-id="45851-147">元素數目的計數器。</span><span class="sxs-lookup"><span data-stu-id="45851-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45851-148">需求</span><span class="sxs-lookup"><span data-stu-id="45851-148">Requirements</span></span>  
 <span data-ttu-id="45851-149">**標頭：** alink.h</span><span class="sxs-lookup"><span data-stu-id="45851-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="45851-150">**程式庫**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="45851-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45851-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45851-151">See also</span></span>

- [<span data-ttu-id="45851-152">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="45851-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
