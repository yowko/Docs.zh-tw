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
# <a name="iceegen-interface"></a><span data-ttu-id="93fa4-102">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="93fa4-102">ICeeGen Interface</span></span>
<span data-ttu-id="93fa4-103">提供動態程式碼編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="93fa4-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="93fa4-104">這個介面已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="93fa4-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93fa4-105">方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-105">Methods</span></span>  
  
|<span data-ttu-id="93fa4-106">方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-106">Method</span></span>|<span data-ttu-id="93fa4-107">描述</span><span class="sxs-lookup"><span data-stu-id="93fa4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93fa4-108">AddSectionReloc 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-108">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|<span data-ttu-id="93fa4-109">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-109">Obsolete.</span></span> <span data-ttu-id="93fa4-110">將 reloc 指令新增至程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="93fa4-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="93fa4-111">AllocateMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-111">AllocateMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="93fa4-112">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-112">Obsolete.</span></span> <span data-ttu-id="93fa4-113">為方法建立指定大小的緩衝區，並取得方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="93fa4-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="93fa4-114">ComputePointer 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-114">ComputePointer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|<span data-ttu-id="93fa4-115">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-115">Obsolete.</span></span> <span data-ttu-id="93fa4-116">判斷指定之程式碼區段的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="93fa4-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="93fa4-117">EmitString 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-117">EmitString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|<span data-ttu-id="93fa4-118">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-118">Obsolete.</span></span> <span data-ttu-id="93fa4-119">將指定的字串發出至程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="93fa4-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="93fa4-120">GenerateCeeFile 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-120">GenerateCeeFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|<span data-ttu-id="93fa4-121">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-121">Obsolete.</span></span> <span data-ttu-id="93fa4-122">產生程式碼基底檔案，其中包含目前載入此 `ICeeGen`的程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="93fa4-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="93fa4-123">GenerateCeeMemoryImage 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-123">GenerateCeeMemoryImage Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|<span data-ttu-id="93fa4-124">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-124">Obsolete.</span></span> <span data-ttu-id="93fa4-125">在記憶體中產生程式碼基底的影像。</span><span class="sxs-lookup"><span data-stu-id="93fa4-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="93fa4-126">GetIlSection 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-126">GetIlSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|<span data-ttu-id="93fa4-127">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-127">Obsolete.</span></span> <span data-ttu-id="93fa4-128">取得指定控制碼所參考之中繼語言程式碼基底的區段。</span><span class="sxs-lookup"><span data-stu-id="93fa4-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="93fa4-129">GetIMapTokenIface 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-129">GetIMapTokenIface Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|<span data-ttu-id="93fa4-130">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-130">Obsolete.</span></span> <span data-ttu-id="93fa4-131">取得指定之標記所參考的介面。</span><span class="sxs-lookup"><span data-stu-id="93fa4-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="93fa4-132">GetMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-132">GetMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|<span data-ttu-id="93fa4-133">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-133">Obsolete.</span></span> <span data-ttu-id="93fa4-134">取得在指定的相對虛擬位址上，方法之適當大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="93fa4-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="93fa4-135">GetSectionBlock 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-135">GetSectionBlock Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|<span data-ttu-id="93fa4-136">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-136">Obsolete.</span></span> <span data-ttu-id="93fa4-137">取得程式碼基底的區段區塊。</span><span class="sxs-lookup"><span data-stu-id="93fa4-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="93fa4-138">GetSectionCreate 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-138">GetSectionCreate Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|<span data-ttu-id="93fa4-139">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-139">Obsolete.</span></span> <span data-ttu-id="93fa4-140">使用指定的名稱和旗標值，產生並取得程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="93fa4-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="93fa4-141">GetSectionDataLen 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-141">GetSectionDataLen Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|<span data-ttu-id="93fa4-142">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-142">Obsolete.</span></span> <span data-ttu-id="93fa4-143">取得指定區段的長度。</span><span class="sxs-lookup"><span data-stu-id="93fa4-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="93fa4-144">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-144">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|<span data-ttu-id="93fa4-145">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-145">Obsolete.</span></span> <span data-ttu-id="93fa4-146">取得儲存在指定之相對虛擬位址的字串。</span><span class="sxs-lookup"><span data-stu-id="93fa4-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="93fa4-147">GetStringSection 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-147">GetStringSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|<span data-ttu-id="93fa4-148">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-148">Obsolete.</span></span> <span data-ttu-id="93fa4-149">取得指定控制碼所參考之程式碼區段的字串表示。</span><span class="sxs-lookup"><span data-stu-id="93fa4-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="93fa4-150">TruncateSection 方法</span><span class="sxs-lookup"><span data-stu-id="93fa4-150">TruncateSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|<span data-ttu-id="93fa4-151">已過時。</span><span class="sxs-lookup"><span data-stu-id="93fa4-151">Obsolete.</span></span> <span data-ttu-id="93fa4-152">依指定的長度截斷指定的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="93fa4-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93fa4-153">需求</span><span class="sxs-lookup"><span data-stu-id="93fa4-153">Requirements</span></span>  
 <span data-ttu-id="93fa4-154">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93fa4-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93fa4-155">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="93fa4-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="93fa4-156">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="93fa4-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="93fa4-157">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93fa4-157">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93fa4-158">請參閱</span><span class="sxs-lookup"><span data-stu-id="93fa4-158">See also</span></span>

- [<span data-ttu-id="93fa4-159">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="93fa4-159">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
