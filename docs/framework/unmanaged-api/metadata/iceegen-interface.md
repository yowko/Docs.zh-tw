---
title: ICeeGen 介面
ms.date: 03/30/2017
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
ms.openlocfilehash: ae3c372951de00b097d0a8437039a3a85bf3aabf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426159"
---
# <a name="iceegen-interface"></a><span data-ttu-id="61164-102">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="61164-102">ICeeGen Interface</span></span>
<span data-ttu-id="61164-103">提供動態程式碼編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="61164-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="61164-104">This interface is obsolete and should not be used.</span><span class="sxs-lookup"><span data-stu-id="61164-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61164-105">方法</span><span class="sxs-lookup"><span data-stu-id="61164-105">Methods</span></span>  
  
|<span data-ttu-id="61164-106">方法</span><span class="sxs-lookup"><span data-stu-id="61164-106">Method</span></span>|<span data-ttu-id="61164-107">描述</span><span class="sxs-lookup"><span data-stu-id="61164-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="61164-108">AddSectionReloc 方法</span><span class="sxs-lookup"><span data-stu-id="61164-108">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|<span data-ttu-id="61164-109">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-109">Obsolete.</span></span> <span data-ttu-id="61164-110">Adds a .reloc instruction to the code base.</span><span class="sxs-lookup"><span data-stu-id="61164-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="61164-111">AllocateMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="61164-111">AllocateMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="61164-112">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-112">Obsolete.</span></span> <span data-ttu-id="61164-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span><span class="sxs-lookup"><span data-stu-id="61164-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="61164-114">ComputePointer 方法</span><span class="sxs-lookup"><span data-stu-id="61164-114">ComputePointer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|<span data-ttu-id="61164-115">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-115">Obsolete.</span></span> <span data-ttu-id="61164-116">Determines the buffer for the specified code section.</span><span class="sxs-lookup"><span data-stu-id="61164-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="61164-117">EmitString 方法</span><span class="sxs-lookup"><span data-stu-id="61164-117">EmitString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|<span data-ttu-id="61164-118">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-118">Obsolete.</span></span> <span data-ttu-id="61164-119">Emits the specified string into the code base.</span><span class="sxs-lookup"><span data-stu-id="61164-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="61164-120">GenerateCeeFile 方法</span><span class="sxs-lookup"><span data-stu-id="61164-120">GenerateCeeFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|<span data-ttu-id="61164-121">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-121">Obsolete.</span></span> <span data-ttu-id="61164-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span><span class="sxs-lookup"><span data-stu-id="61164-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="61164-123">GenerateCeeMemoryImage 方法</span><span class="sxs-lookup"><span data-stu-id="61164-123">GenerateCeeMemoryImage Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|<span data-ttu-id="61164-124">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-124">Obsolete.</span></span> <span data-ttu-id="61164-125">Generates an image in memory for the code base.</span><span class="sxs-lookup"><span data-stu-id="61164-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="61164-126">GetIlSection 方法</span><span class="sxs-lookup"><span data-stu-id="61164-126">GetIlSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|<span data-ttu-id="61164-127">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-127">Obsolete.</span></span> <span data-ttu-id="61164-128">Gets the section of the intermediate language code base referenced by the specified handle.</span><span class="sxs-lookup"><span data-stu-id="61164-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="61164-129">GetIMapTokenIface 方法</span><span class="sxs-lookup"><span data-stu-id="61164-129">GetIMapTokenIface Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|<span data-ttu-id="61164-130">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-130">Obsolete.</span></span> <span data-ttu-id="61164-131">Gets the interface referenced by the specified token.</span><span class="sxs-lookup"><span data-stu-id="61164-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="61164-132">GetMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="61164-132">GetMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|<span data-ttu-id="61164-133">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-133">Obsolete.</span></span> <span data-ttu-id="61164-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span><span class="sxs-lookup"><span data-stu-id="61164-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="61164-135">GetSectionBlock 方法</span><span class="sxs-lookup"><span data-stu-id="61164-135">GetSectionBlock Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|<span data-ttu-id="61164-136">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-136">Obsolete.</span></span> <span data-ttu-id="61164-137">Gets a section block of the code base.</span><span class="sxs-lookup"><span data-stu-id="61164-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="61164-138">GetSectionCreate 方法</span><span class="sxs-lookup"><span data-stu-id="61164-138">GetSectionCreate Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|<span data-ttu-id="61164-139">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-139">Obsolete.</span></span> <span data-ttu-id="61164-140">Generates and gets a code section using the specified name and flag values.</span><span class="sxs-lookup"><span data-stu-id="61164-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="61164-141">GetSectionDataLen 方法</span><span class="sxs-lookup"><span data-stu-id="61164-141">GetSectionDataLen Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|<span data-ttu-id="61164-142">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-142">Obsolete.</span></span> <span data-ttu-id="61164-143">Gets the length of the specified section.</span><span class="sxs-lookup"><span data-stu-id="61164-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="61164-144">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="61164-144">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|<span data-ttu-id="61164-145">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-145">Obsolete.</span></span> <span data-ttu-id="61164-146">Gets the string stored at the specified relative virtual address.</span><span class="sxs-lookup"><span data-stu-id="61164-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="61164-147">GetStringSection 方法</span><span class="sxs-lookup"><span data-stu-id="61164-147">GetStringSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|<span data-ttu-id="61164-148">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-148">Obsolete.</span></span> <span data-ttu-id="61164-149">Gets a string representation of the code section referenced by the specified handle.</span><span class="sxs-lookup"><span data-stu-id="61164-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="61164-150">TruncateSection 方法</span><span class="sxs-lookup"><span data-stu-id="61164-150">TruncateSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|<span data-ttu-id="61164-151">已過時。</span><span class="sxs-lookup"><span data-stu-id="61164-151">Obsolete.</span></span> <span data-ttu-id="61164-152">Truncates the specified code section by the specified length.</span><span class="sxs-lookup"><span data-stu-id="61164-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61164-153">需求</span><span class="sxs-lookup"><span data-stu-id="61164-153">Requirements</span></span>  
 <span data-ttu-id="61164-154">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61164-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61164-155">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="61164-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61164-156">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61164-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="61164-157">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61164-157">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61164-158">請參閱</span><span class="sxs-lookup"><span data-stu-id="61164-158">See also</span></span>

- [<span data-ttu-id="61164-159">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="61164-159">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
