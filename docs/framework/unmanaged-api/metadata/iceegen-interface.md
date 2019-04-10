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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fb081c48abf899b44da1c1351efa3f6036f1c8d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176120"
---
# <a name="iceegen-interface"></a><span data-ttu-id="cd383-102">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="cd383-102">ICeeGen Interface</span></span>
<span data-ttu-id="cd383-103">提供動態程式碼編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="cd383-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="cd383-104">這個介面已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="cd383-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd383-105">方法</span><span class="sxs-lookup"><span data-stu-id="cd383-105">Methods</span></span>  
  
|<span data-ttu-id="cd383-106">方法</span><span class="sxs-lookup"><span data-stu-id="cd383-106">Method</span></span>|<span data-ttu-id="cd383-107">描述</span><span class="sxs-lookup"><span data-stu-id="cd383-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd383-108">AddSectionReloc 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-108">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|<span data-ttu-id="cd383-109">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-109">Obsolete.</span></span> <span data-ttu-id="cd383-110">將程式碼基底.reloc 指令。</span><span class="sxs-lookup"><span data-stu-id="cd383-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="cd383-111">AllocateMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-111">AllocateMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="cd383-112">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-112">Obsolete.</span></span> <span data-ttu-id="cd383-113">建立方法中，指定大小的緩衝區，並取得方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="cd383-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="cd383-114">ComputePointer 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-114">ComputePointer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|<span data-ttu-id="cd383-115">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-115">Obsolete.</span></span> <span data-ttu-id="cd383-116">判斷指定的程式碼區段的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="cd383-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="cd383-117">EmitString 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-117">EmitString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|<span data-ttu-id="cd383-118">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-118">Obsolete.</span></span> <span data-ttu-id="cd383-119">程式碼基底到發出指定的字串。</span><span class="sxs-lookup"><span data-stu-id="cd383-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="cd383-120">GenerateCeeFile 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-120">GenerateCeeFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|<span data-ttu-id="cd383-121">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-121">Obsolete.</span></span> <span data-ttu-id="cd383-122">產生程式碼基底檔案，其中包含目前載入到這個程式碼基底`ICeeGen`。</span><span class="sxs-lookup"><span data-stu-id="cd383-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="cd383-123">GenerateCeeMemoryImage 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-123">GenerateCeeMemoryImage Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|<span data-ttu-id="cd383-124">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-124">Obsolete.</span></span> <span data-ttu-id="cd383-125">在記憶體中的程式碼基底，會產生映像。</span><span class="sxs-lookup"><span data-stu-id="cd383-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="cd383-126">GetIlSection 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-126">GetIlSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|<span data-ttu-id="cd383-127">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-127">Obsolete.</span></span> <span data-ttu-id="cd383-128">取得指定的控制代碼所參考的基底中繼語言程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="cd383-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="cd383-129">GetIMapTokenIface 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-129">GetIMapTokenIface Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|<span data-ttu-id="cd383-130">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-130">Obsolete.</span></span> <span data-ttu-id="cd383-131">取得指定語彙基元所參考的介面。</span><span class="sxs-lookup"><span data-stu-id="cd383-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="cd383-132">GetMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-132">GetMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|<span data-ttu-id="cd383-133">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-133">Obsolete.</span></span> <span data-ttu-id="cd383-134">取得方法的適當大小的緩衝區，在指定的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="cd383-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="cd383-135">GetSectionBlock 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-135">GetSectionBlock Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|<span data-ttu-id="cd383-136">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-136">Obsolete.</span></span> <span data-ttu-id="cd383-137">取得區段的區塊程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="cd383-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="cd383-138">GetSectionCreate 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-138">GetSectionCreate Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|<span data-ttu-id="cd383-139">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-139">Obsolete.</span></span> <span data-ttu-id="cd383-140">產生並取得使用指定的名稱和旗標值的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="cd383-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="cd383-141">GetSectionDataLen 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-141">GetSectionDataLen Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|<span data-ttu-id="cd383-142">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-142">Obsolete.</span></span> <span data-ttu-id="cd383-143">取得指定的區段長度。</span><span class="sxs-lookup"><span data-stu-id="cd383-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="cd383-144">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-144">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|<span data-ttu-id="cd383-145">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-145">Obsolete.</span></span> <span data-ttu-id="cd383-146">取得儲存在指定的相對虛擬位址的字串。</span><span class="sxs-lookup"><span data-stu-id="cd383-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="cd383-147">GetStringSection 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-147">GetStringSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|<span data-ttu-id="cd383-148">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-148">Obsolete.</span></span> <span data-ttu-id="cd383-149">取得指定的控制代碼所參考的程式碼區段的字串表示。</span><span class="sxs-lookup"><span data-stu-id="cd383-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="cd383-150">TruncateSection 方法</span><span class="sxs-lookup"><span data-stu-id="cd383-150">TruncateSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|<span data-ttu-id="cd383-151">已過時。</span><span class="sxs-lookup"><span data-stu-id="cd383-151">Obsolete.</span></span> <span data-ttu-id="cd383-152">將指定的程式碼區段捨去指定的長度。</span><span class="sxs-lookup"><span data-stu-id="cd383-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd383-153">需求</span><span class="sxs-lookup"><span data-stu-id="cd383-153">Requirements</span></span>  
 <span data-ttu-id="cd383-154">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd383-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd383-155">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd383-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd383-156">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cd383-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="cd383-157">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="cd383-157">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cd383-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd383-158">See also</span></span>

- [<span data-ttu-id="cd383-159">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="cd383-159">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
