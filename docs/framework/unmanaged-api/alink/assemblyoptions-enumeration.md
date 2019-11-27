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
ms.openlocfilehash: ed45e06297b77ea60304cdcfe1b08e97f9e4c085
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446596"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="75a7e-102">AssemblyOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="75a7e-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="75a7e-103">列舉元件選項。</span><span class="sxs-lookup"><span data-stu-id="75a7e-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75a7e-104">語法</span><span class="sxs-lookup"><span data-stu-id="75a7e-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="75a7e-105">欄位</span><span class="sxs-lookup"><span data-stu-id="75a7e-105">Fields</span></span>  
  
|<span data-ttu-id="75a7e-106">欄位</span><span class="sxs-lookup"><span data-stu-id="75a7e-106">Field</span></span>|<span data-ttu-id="75a7e-107">描述</span><span class="sxs-lookup"><span data-stu-id="75a7e-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="75a7e-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="75a7e-108">optAssemTitle</span></span>|<span data-ttu-id="75a7e-109">String-表示元件標題。</span><span class="sxs-lookup"><span data-stu-id="75a7e-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="75a7e-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="75a7e-110">optAssemDescription</span></span>|<span data-ttu-id="75a7e-111">String-包含元件描述。</span><span class="sxs-lookup"><span data-stu-id="75a7e-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="75a7e-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="75a7e-112">optAssemConfig</span></span>|<span data-ttu-id="75a7e-113">String-包含元件設定。</span><span class="sxs-lookup"><span data-stu-id="75a7e-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="75a7e-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="75a7e-114">optAssemOS</span></span>|<span data-ttu-id="75a7e-115">字串編碼為： "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion"。</span><span class="sxs-lookup"><span data-stu-id="75a7e-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="75a7e-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="75a7e-116">optAssemProcessor</span></span>|<span data-ttu-id="75a7e-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="75a7e-117">ULONG</span></span>|  
|<span data-ttu-id="75a7e-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="75a7e-118">optAssemLocale</span></span>|<span data-ttu-id="75a7e-119">String-包含元件地區設定。</span><span class="sxs-lookup"><span data-stu-id="75a7e-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="75a7e-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="75a7e-120">optAssemVersion</span></span>|<span data-ttu-id="75a7e-121">字串編碼為：「主要. 次要. 組建. 修訂」。</span><span class="sxs-lookup"><span data-stu-id="75a7e-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="75a7e-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="75a7e-122">optAssemCompany</span></span>|<span data-ttu-id="75a7e-123">String-包含公司。</span><span class="sxs-lookup"><span data-stu-id="75a7e-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="75a7e-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="75a7e-124">optAssemProduct</span></span>|<span data-ttu-id="75a7e-125">String-包含產品名稱。</span><span class="sxs-lookup"><span data-stu-id="75a7e-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="75a7e-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="75a7e-126">optAssemProductVersion</span></span>|<span data-ttu-id="75a7e-127">String （也稱為 InformationalVersion）。</span><span class="sxs-lookup"><span data-stu-id="75a7e-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="75a7e-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="75a7e-128">optAssemCopyright</span></span>|<span data-ttu-id="75a7e-129">String-包含著作權資訊。</span><span class="sxs-lookup"><span data-stu-id="75a7e-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="75a7e-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="75a7e-130">optAssemTrademark</span></span>|<span data-ttu-id="75a7e-131">String-包含商標資訊。</span><span class="sxs-lookup"><span data-stu-id="75a7e-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="75a7e-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="75a7e-132">optAssemKeyFile</span></span>|<span data-ttu-id="75a7e-133">字串（檔案名）。</span><span class="sxs-lookup"><span data-stu-id="75a7e-133">String (file name).</span></span>|  
|<span data-ttu-id="75a7e-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="75a7e-134">optAssemKeyName</span></span>|<span data-ttu-id="75a7e-135">字串（索引鍵名稱）。</span><span class="sxs-lookup"><span data-stu-id="75a7e-135">String (The key name).</span></span>|  
|<span data-ttu-id="75a7e-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="75a7e-136">optAssemAlgID</span></span>|<span data-ttu-id="75a7e-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="75a7e-137">ULONG</span></span>|  
|<span data-ttu-id="75a7e-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="75a7e-138">optAssemFlags</span></span>|<span data-ttu-id="75a7e-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="75a7e-139">ULONG</span></span>|  
|<span data-ttu-id="75a7e-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="75a7e-140">optAssemHalfSign</span></span>|<span data-ttu-id="75a7e-141">Bool （也稱為 DelaySign）。</span><span class="sxs-lookup"><span data-stu-id="75a7e-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="75a7e-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="75a7e-142">optAssemFileVersion</span></span>|<span data-ttu-id="75a7e-143">字串編碼為「主要. 次要. 組建修訂版」--與 ProductVersion 相同。</span><span class="sxs-lookup"><span data-stu-id="75a7e-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="75a7e-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="75a7e-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="75a7e-145">字串編碼為「主要. 次要. 組建. 修訂」。</span><span class="sxs-lookup"><span data-stu-id="75a7e-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="75a7e-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="75a7e-146">optLastAssemOption</span></span>|<span data-ttu-id="75a7e-147">元素數目的計數器。</span><span class="sxs-lookup"><span data-stu-id="75a7e-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75a7e-148">需求</span><span class="sxs-lookup"><span data-stu-id="75a7e-148">Requirements</span></span>  
 <span data-ttu-id="75a7e-149">**標頭：** alink。h</span><span class="sxs-lookup"><span data-stu-id="75a7e-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="75a7e-150">連結**庫**： alink .dll</span><span class="sxs-lookup"><span data-stu-id="75a7e-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75a7e-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75a7e-151">See also</span></span>

- [<span data-ttu-id="75a7e-152">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="75a7e-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
