---
title: "ICeeGen 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 73af58ac55fd22e5b4f19f715cb0b1a137a640a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iceegen-interface"></a><span data-ttu-id="51c6a-102">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="51c6a-102">ICeeGen Interface</span></span>
<span data-ttu-id="51c6a-103">提供動態程式碼編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="51c6a-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="51c6a-104">這個介面已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="51c6a-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51c6a-105">方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-105">Methods</span></span>  
  
|<span data-ttu-id="51c6a-106">方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-106">Method</span></span>|<span data-ttu-id="51c6a-107">描述</span><span class="sxs-lookup"><span data-stu-id="51c6a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51c6a-108">AddSectionReloc 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-108">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|<span data-ttu-id="51c6a-109">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-109">Obsolete.</span></span> <span data-ttu-id="51c6a-110">將程式碼基底.reloc 指令。</span><span class="sxs-lookup"><span data-stu-id="51c6a-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="51c6a-111">AllocateMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-111">AllocateMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="51c6a-112">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-112">Obsolete.</span></span> <span data-ttu-id="51c6a-113">建立方法，指定大小的緩衝區，並取得方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="51c6a-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="51c6a-114">ComputePointer 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-114">ComputePointer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|<span data-ttu-id="51c6a-115">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-115">Obsolete.</span></span> <span data-ttu-id="51c6a-116">判斷指定的程式碼區段的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="51c6a-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="51c6a-117">EmitString 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-117">EmitString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|<span data-ttu-id="51c6a-118">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-118">Obsolete.</span></span> <span data-ttu-id="51c6a-119">指定的字串發出到程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="51c6a-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="51c6a-120">GenerateCeeFile 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-120">GenerateCeeFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|<span data-ttu-id="51c6a-121">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-121">Obsolete.</span></span> <span data-ttu-id="51c6a-122">產生程式碼基底檔案，其中包含目前載入到這個程式碼基底`ICeeGen`。</span><span class="sxs-lookup"><span data-stu-id="51c6a-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="51c6a-123">GenerateCeeMemoryImage 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-123">GenerateCeeMemoryImage Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|<span data-ttu-id="51c6a-124">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-124">Obsolete.</span></span> <span data-ttu-id="51c6a-125">在記憶體中的程式碼基底產生影像。</span><span class="sxs-lookup"><span data-stu-id="51c6a-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="51c6a-126">GetIlSection 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-126">GetIlSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|<span data-ttu-id="51c6a-127">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-127">Obsolete.</span></span> <span data-ttu-id="51c6a-128">取得指定的控制代碼所參考的基底中繼語言程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="51c6a-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="51c6a-129">GetIMapTokenIface 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-129">GetIMapTokenIface Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|<span data-ttu-id="51c6a-130">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-130">Obsolete.</span></span> <span data-ttu-id="51c6a-131">取得指定語彙基元所參考的介面。</span><span class="sxs-lookup"><span data-stu-id="51c6a-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="51c6a-132">GetMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-132">GetMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|<span data-ttu-id="51c6a-133">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-133">Obsolete.</span></span> <span data-ttu-id="51c6a-134">在指定的相對虛擬位址的方法取得適當大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="51c6a-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="51c6a-135">GetSectionBlock 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-135">GetSectionBlock Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|<span data-ttu-id="51c6a-136">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-136">Obsolete.</span></span> <span data-ttu-id="51c6a-137">取得區段的區塊程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="51c6a-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="51c6a-138">GetSectionCreate 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-138">GetSectionCreate Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|<span data-ttu-id="51c6a-139">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-139">Obsolete.</span></span> <span data-ttu-id="51c6a-140">產生並取得使用指定的名稱和旗標值的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="51c6a-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="51c6a-141">GetSectionDataLen 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-141">GetSectionDataLen Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|<span data-ttu-id="51c6a-142">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-142">Obsolete.</span></span> <span data-ttu-id="51c6a-143">取得指定之區段的長度。</span><span class="sxs-lookup"><span data-stu-id="51c6a-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="51c6a-144">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-144">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|<span data-ttu-id="51c6a-145">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-145">Obsolete.</span></span> <span data-ttu-id="51c6a-146">取得儲存在指定的相對虛擬位址的字串。</span><span class="sxs-lookup"><span data-stu-id="51c6a-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="51c6a-147">GetStringSection 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-147">GetStringSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|<span data-ttu-id="51c6a-148">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-148">Obsolete.</span></span> <span data-ttu-id="51c6a-149">取得指定的控制代碼所參考的程式碼區段的字串表示。</span><span class="sxs-lookup"><span data-stu-id="51c6a-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="51c6a-150">TruncateSection 方法</span><span class="sxs-lookup"><span data-stu-id="51c6a-150">TruncateSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|<span data-ttu-id="51c6a-151">已過時。</span><span class="sxs-lookup"><span data-stu-id="51c6a-151">Obsolete.</span></span> <span data-ttu-id="51c6a-152">指定的長度來截斷指定的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="51c6a-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51c6a-153">需求</span><span class="sxs-lookup"><span data-stu-id="51c6a-153">Requirements</span></span>  
 <span data-ttu-id="51c6a-154">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51c6a-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51c6a-155">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="51c6a-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51c6a-156">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="51c6a-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51c6a-157">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51c6a-157">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c6a-158">請參閱</span><span class="sxs-lookup"><span data-stu-id="51c6a-158">See Also</span></span>  
 [<span data-ttu-id="51c6a-159">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="51c6a-159">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
