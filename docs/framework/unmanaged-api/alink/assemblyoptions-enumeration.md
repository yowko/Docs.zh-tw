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
ms.openlocfilehash: 49e7b73559e8def890f8df8f596fbe8ad5bb5d3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777476"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="fb3cb-102">AssemblyOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="fb3cb-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="fb3cb-103">列舉元件選項。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb3cb-104">語法</span><span class="sxs-lookup"><span data-stu-id="fb3cb-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="fb3cb-105">欄位</span><span class="sxs-lookup"><span data-stu-id="fb3cb-105">Fields</span></span>  
  
|<span data-ttu-id="fb3cb-106">欄位</span><span class="sxs-lookup"><span data-stu-id="fb3cb-106">Field</span></span>|<span data-ttu-id="fb3cb-107">描述</span><span class="sxs-lookup"><span data-stu-id="fb3cb-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fb3cb-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="fb3cb-108">optAssemTitle</span></span>|<span data-ttu-id="fb3cb-109">String-表示元件標題。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="fb3cb-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="fb3cb-110">optAssemDescription</span></span>|<span data-ttu-id="fb3cb-111">String-包含元件描述。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="fb3cb-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="fb3cb-112">optAssemConfig</span></span>|<span data-ttu-id="fb3cb-113">String-包含元件設定。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="fb3cb-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="fb3cb-114">optAssemOS</span></span>|<span data-ttu-id="fb3cb-115">字串編碼為： "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion"。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="fb3cb-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="fb3cb-116">optAssemProcessor</span></span>|<span data-ttu-id="fb3cb-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="fb3cb-117">ULONG</span></span>|  
|<span data-ttu-id="fb3cb-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="fb3cb-118">optAssemLocale</span></span>|<span data-ttu-id="fb3cb-119">String-包含元件地區設定。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="fb3cb-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="fb3cb-120">optAssemVersion</span></span>|<span data-ttu-id="fb3cb-121">字串編碼為：「主要. 次要. 組建修訂」。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="fb3cb-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="fb3cb-122">optAssemCompany</span></span>|<span data-ttu-id="fb3cb-123">String-包含公司。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="fb3cb-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="fb3cb-124">optAssemProduct</span></span>|<span data-ttu-id="fb3cb-125">String-包含產品名稱。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="fb3cb-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="fb3cb-126">optAssemProductVersion</span></span>|<span data-ttu-id="fb3cb-127">String （也稱為 InformationalVersion）。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="fb3cb-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="fb3cb-128">optAssemCopyright</span></span>|<span data-ttu-id="fb3cb-129">String-包含著作權資訊。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="fb3cb-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="fb3cb-130">optAssemTrademark</span></span>|<span data-ttu-id="fb3cb-131">String-包含商標資訊。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="fb3cb-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="fb3cb-132">optAssemKeyFile</span></span>|<span data-ttu-id="fb3cb-133">字串（檔案名）。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-133">String (file name).</span></span>|  
|<span data-ttu-id="fb3cb-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="fb3cb-134">optAssemKeyName</span></span>|<span data-ttu-id="fb3cb-135">字串（索引鍵名稱）。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-135">String (The key name).</span></span>|  
|<span data-ttu-id="fb3cb-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="fb3cb-136">optAssemAlgID</span></span>|<span data-ttu-id="fb3cb-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="fb3cb-137">ULONG</span></span>|  
|<span data-ttu-id="fb3cb-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="fb3cb-138">optAssemFlags</span></span>|<span data-ttu-id="fb3cb-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="fb3cb-139">ULONG</span></span>|  
|<span data-ttu-id="fb3cb-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="fb3cb-140">optAssemHalfSign</span></span>|<span data-ttu-id="fb3cb-141">Bool （也稱為 DelaySign）。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="fb3cb-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="fb3cb-142">optAssemFileVersion</span></span>|<span data-ttu-id="fb3cb-143">字串編碼為「主要. 次要. 組建修訂版」--與 ProductVersion 相同。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="fb3cb-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="fb3cb-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="fb3cb-145">字串編碼為「主要. 次要. 組建. 修訂」。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="fb3cb-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="fb3cb-146">optLastAssemOption</span></span>|<span data-ttu-id="fb3cb-147">元素數目的計數器。</span><span class="sxs-lookup"><span data-stu-id="fb3cb-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb3cb-148">需求</span><span class="sxs-lookup"><span data-stu-id="fb3cb-148">Requirements</span></span>  
 <span data-ttu-id="fb3cb-149">**標頭：** alink。h</span><span class="sxs-lookup"><span data-stu-id="fb3cb-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="fb3cb-150">連結**庫**： alink .dll</span><span class="sxs-lookup"><span data-stu-id="fb3cb-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb3cb-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb3cb-151">See also</span></span>

- [<span data-ttu-id="fb3cb-152">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="fb3cb-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
