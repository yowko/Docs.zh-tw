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
ms.openlocfilehash: e6cf0aa6f731d0a417e1a2be0ca1d0f8c9299379
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008270"
---
# <a name="iceegen-interface"></a><span data-ttu-id="f3bc1-102">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="f3bc1-102">ICeeGen Interface</span></span>
<span data-ttu-id="f3bc1-103">提供動態程式碼編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="f3bc1-104">這個介面已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3bc1-105">方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-105">Methods</span></span>  
  
|<span data-ttu-id="f3bc1-106">方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-106">Method</span></span>|<span data-ttu-id="f3bc1-107">描述</span><span class="sxs-lookup"><span data-stu-id="f3bc1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3bc1-108">AddSectionReloc 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-108">AddSectionReloc Method</span></span>](iceegen-addsectionreloc-method.md)|<span data-ttu-id="f3bc1-109">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-109">Obsolete.</span></span> <span data-ttu-id="f3bc1-110">將 reloc 指令新增至程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="f3bc1-111">AllocateMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-111">AllocateMethodBuffer Method</span></span>](iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="f3bc1-112">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-112">Obsolete.</span></span> <span data-ttu-id="f3bc1-113">為方法建立指定大小的緩衝區，並取得方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="f3bc1-114">ComputePointer 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-114">ComputePointer Method</span></span>](iceegen-computepointer-method.md)|<span data-ttu-id="f3bc1-115">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-115">Obsolete.</span></span> <span data-ttu-id="f3bc1-116">判斷指定之程式碼區段的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="f3bc1-117">EmitString 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-117">EmitString Method</span></span>](iceegen-emitstring-method.md)|<span data-ttu-id="f3bc1-118">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-118">Obsolete.</span></span> <span data-ttu-id="f3bc1-119">將指定的字串發出至程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="f3bc1-120">GenerateCeeFile 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-120">GenerateCeeFile Method</span></span>](iceegen-generateceefile-method.md)|<span data-ttu-id="f3bc1-121">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-121">Obsolete.</span></span> <span data-ttu-id="f3bc1-122">產生程式碼基底檔案，其中包含目前載入此中的程式碼基底 `ICeeGen` 。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="f3bc1-123">GenerateCeeMemoryImage 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-123">GenerateCeeMemoryImage Method</span></span>](iceegen-generateceememoryimage-method.md)|<span data-ttu-id="f3bc1-124">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-124">Obsolete.</span></span> <span data-ttu-id="f3bc1-125">在記憶體中產生程式碼基底的影像。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="f3bc1-126">GetIlSection 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-126">GetIlSection Method</span></span>](iceegen-getilsection-method.md)|<span data-ttu-id="f3bc1-127">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-127">Obsolete.</span></span> <span data-ttu-id="f3bc1-128">取得指定控制碼所參考之中繼語言程式碼基底的區段。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="f3bc1-129">GetIMapTokenIface 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-129">GetIMapTokenIface Method</span></span>](iceegen-getimaptokeniface-method.md)|<span data-ttu-id="f3bc1-130">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-130">Obsolete.</span></span> <span data-ttu-id="f3bc1-131">取得指定之標記所參考的介面。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="f3bc1-132">GetMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-132">GetMethodBuffer Method</span></span>](iceegen-getmethodbuffer-method.md)|<span data-ttu-id="f3bc1-133">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-133">Obsolete.</span></span> <span data-ttu-id="f3bc1-134">取得在指定的相對虛擬位址上，方法之適當大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="f3bc1-135">GetSectionBlock 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-135">GetSectionBlock Method</span></span>](iceegen-getsectionblock-method.md)|<span data-ttu-id="f3bc1-136">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-136">Obsolete.</span></span> <span data-ttu-id="f3bc1-137">取得程式碼基底的區段區塊。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="f3bc1-138">GetSectionCreate 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-138">GetSectionCreate Method</span></span>](iceegen-getsectioncreate-method.md)|<span data-ttu-id="f3bc1-139">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-139">Obsolete.</span></span> <span data-ttu-id="f3bc1-140">使用指定的名稱和旗標值，產生並取得程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="f3bc1-141">GetSectionDataLen 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-141">GetSectionDataLen Method</span></span>](iceegen-getsectiondatalen-method.md)|<span data-ttu-id="f3bc1-142">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-142">Obsolete.</span></span> <span data-ttu-id="f3bc1-143">取得指定區段的長度。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="f3bc1-144">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-144">GetString Method</span></span>](iceegen-getstring-method.md)|<span data-ttu-id="f3bc1-145">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-145">Obsolete.</span></span> <span data-ttu-id="f3bc1-146">取得儲存在指定之相對虛擬位址的字串。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="f3bc1-147">GetStringSection 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-147">GetStringSection Method</span></span>](iceegen-getstringsection-method.md)|<span data-ttu-id="f3bc1-148">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-148">Obsolete.</span></span> <span data-ttu-id="f3bc1-149">取得指定控制碼所參考之程式碼區段的字串表示。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="f3bc1-150">TruncateSection 方法</span><span class="sxs-lookup"><span data-stu-id="f3bc1-150">TruncateSection Method</span></span>](iceegen-truncatesection-method.md)|<span data-ttu-id="f3bc1-151">已過時。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-151">Obsolete.</span></span> <span data-ttu-id="f3bc1-152">依指定的長度截斷指定的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f3bc1-153">需求</span><span class="sxs-lookup"><span data-stu-id="f3bc1-153">Requirements</span></span>  
 <span data-ttu-id="f3bc1-154">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3bc1-154">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3bc1-155">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="f3bc1-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3bc1-156">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="f3bc1-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3bc1-157">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3bc1-157">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3bc1-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3bc1-158">See also</span></span>

- [<span data-ttu-id="f3bc1-159">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="f3bc1-159">Metadata Interfaces</span></span>](metadata-interfaces.md)
