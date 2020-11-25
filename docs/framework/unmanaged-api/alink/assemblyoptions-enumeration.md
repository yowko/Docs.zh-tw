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
ms.openlocfilehash: 352e1acd1fdd8297754e18b2e8c6448ea723a557
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717025"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="01c91-102">AssemblyOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="01c91-102">AssemblyOptions Enumeration</span></span>

<span data-ttu-id="01c91-103">列舉元件選項。</span><span class="sxs-lookup"><span data-stu-id="01c91-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01c91-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="01c91-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="01c91-105">欄位</span><span class="sxs-lookup"><span data-stu-id="01c91-105">Fields</span></span>  
  
|<span data-ttu-id="01c91-106">欄位</span><span class="sxs-lookup"><span data-stu-id="01c91-106">Field</span></span>|<span data-ttu-id="01c91-107">描述</span><span class="sxs-lookup"><span data-stu-id="01c91-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="01c91-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="01c91-108">optAssemTitle</span></span>|<span data-ttu-id="01c91-109">字串-表示元件標題。</span><span class="sxs-lookup"><span data-stu-id="01c91-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="01c91-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="01c91-110">optAssemDescription</span></span>|<span data-ttu-id="01c91-111">字串-包含元件描述。</span><span class="sxs-lookup"><span data-stu-id="01c91-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="01c91-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="01c91-112">optAssemConfig</span></span>|<span data-ttu-id="01c91-113">字串-包含元件設定。</span><span class="sxs-lookup"><span data-stu-id="01c91-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="01c91-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="01c91-114">optAssemOS</span></span>|<span data-ttu-id="01c91-115">字串編碼為： "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion"。</span><span class="sxs-lookup"><span data-stu-id="01c91-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="01c91-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="01c91-116">optAssemProcessor</span></span>|<span data-ttu-id="01c91-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="01c91-117">ULONG</span></span>|  
|<span data-ttu-id="01c91-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="01c91-118">optAssemLocale</span></span>|<span data-ttu-id="01c91-119">字串-包含元件地區設定。</span><span class="sxs-lookup"><span data-stu-id="01c91-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="01c91-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="01c91-120">optAssemVersion</span></span>|<span data-ttu-id="01c91-121">以字串編碼的： "主要。</span><span class="sxs-lookup"><span data-stu-id="01c91-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="01c91-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="01c91-122">optAssemCompany</span></span>|<span data-ttu-id="01c91-123">包含公司的字串。</span><span class="sxs-lookup"><span data-stu-id="01c91-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="01c91-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="01c91-124">optAssemProduct</span></span>|<span data-ttu-id="01c91-125">字串-包含產品名稱。</span><span class="sxs-lookup"><span data-stu-id="01c91-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="01c91-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="01c91-126">optAssemProductVersion</span></span>|<span data-ttu-id="01c91-127">字串 (也稱為 InformationalVersion) 。</span><span class="sxs-lookup"><span data-stu-id="01c91-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="01c91-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="01c91-128">optAssemCopyright</span></span>|<span data-ttu-id="01c91-129">字串-包含著作權資訊。</span><span class="sxs-lookup"><span data-stu-id="01c91-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="01c91-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="01c91-130">optAssemTrademark</span></span>|<span data-ttu-id="01c91-131">字串-包含商標資訊。</span><span class="sxs-lookup"><span data-stu-id="01c91-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="01c91-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="01c91-132">optAssemKeyFile</span></span>|<span data-ttu-id="01c91-133">字串 (的檔案名) 。</span><span class="sxs-lookup"><span data-stu-id="01c91-133">String (file name).</span></span>|  
|<span data-ttu-id="01c91-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="01c91-134">optAssemKeyName</span></span>|<span data-ttu-id="01c91-135"> (索引鍵名稱) 的字串。</span><span class="sxs-lookup"><span data-stu-id="01c91-135">String (The key name).</span></span>|  
|<span data-ttu-id="01c91-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="01c91-136">optAssemAlgID</span></span>|<span data-ttu-id="01c91-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="01c91-137">ULONG</span></span>|  
|<span data-ttu-id="01c91-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="01c91-138">optAssemFlags</span></span>|<span data-ttu-id="01c91-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="01c91-139">ULONG</span></span>|  
|<span data-ttu-id="01c91-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="01c91-140">optAssemHalfSign</span></span>|<span data-ttu-id="01c91-141">Bool (也稱為 DelaySign) 。</span><span class="sxs-lookup"><span data-stu-id="01c91-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="01c91-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="01c91-142">optAssemFileVersion</span></span>|<span data-ttu-id="01c91-143">字串編碼為 "主要... a.. a.. a.. a.. a.. a... a</span><span class="sxs-lookup"><span data-stu-id="01c91-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="01c91-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="01c91-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="01c91-145">以字串編碼為 "主要。</span><span class="sxs-lookup"><span data-stu-id="01c91-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="01c91-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="01c91-146">optLastAssemOption</span></span>|<span data-ttu-id="01c91-147">元素數目的計數器。</span><span class="sxs-lookup"><span data-stu-id="01c91-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01c91-148">需求</span><span class="sxs-lookup"><span data-stu-id="01c91-148">Requirements</span></span>  

 <span data-ttu-id="01c91-149">**標頭：** alink。h</span><span class="sxs-lookup"><span data-stu-id="01c91-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="01c91-150">連結 **庫**： alink.dll</span><span class="sxs-lookup"><span data-stu-id="01c91-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01c91-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01c91-151">See also</span></span>

- [<span data-ttu-id="01c91-152">Al.exe (元件連結器) </span><span class="sxs-lookup"><span data-stu-id="01c91-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
