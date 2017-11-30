---
title: "ICorDebugSymbolProvider2::GetGenericDictionaryInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0c4192c94d70bd9406607d645716e4dd6f8b957
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="2846f-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo 方法</span><span class="sxs-lookup"><span data-stu-id="2846f-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>
<span data-ttu-id="2846f-103">擷取泛型字典對應。</span><span class="sxs-lookup"><span data-stu-id="2846f-103">Retrieves a generic dictionary map.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2846f-104">語法</span><span class="sxs-lookup"><span data-stu-id="2846f-104">Syntax</span></span>  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2846f-105">參數</span><span class="sxs-lookup"><span data-stu-id="2846f-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="2846f-106">[out]位址指標[ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)物件，其中包含泛型字典對應。</span><span class="sxs-lookup"><span data-stu-id="2846f-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="2846f-107">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="2846f-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2846f-108">備註</span><span class="sxs-lookup"><span data-stu-id="2846f-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2846f-109">這個方法僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="2846f-109">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="2846f-110">對應是由兩個最上層區段所組成：</span><span class="sxs-lookup"><span data-stu-id="2846f-110">The map consists of two top-level sections:</span></span>  
  
-   <span data-ttu-id="2846f-111">A[目錄](#Directory)包含此對應中所有字典的相對虛擬位址 (RVA)。</span><span class="sxs-lookup"><span data-stu-id="2846f-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>  
  
-   <span data-ttu-id="2846f-112">位元組對齊[堆積](#Heap)，其中包含物件具現化資訊。</span><span class="sxs-lookup"><span data-stu-id="2846f-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="2846f-113">會在最後一個目錄項目之後立即啟動。</span><span class="sxs-lookup"><span data-stu-id="2846f-113">It starts immediately after the last directory entry.</span></span>  
  
<a name="Directory"></a>   
## <a name="the-directory"></a><span data-ttu-id="2846f-114">目錄</span><span class="sxs-lookup"><span data-stu-id="2846f-114">The Directory</span></span>  
 <span data-ttu-id="2846f-115">目錄中的每個項目是指堆積中的位移，也就是相對於堆積開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="2846f-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="2846f-116">個別項目的值不一定是唯一的，可能會有多個目錄項目指向堆積中的同一個位移。</span><span class="sxs-lookup"><span data-stu-id="2846f-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>  
  
 <span data-ttu-id="2846f-117">泛型字典對應的目錄部分具有下列結構：</span><span class="sxs-lookup"><span data-stu-id="2846f-117">The directory portion of the generic dictionary map has the following structure:</span></span>  
  
-   <span data-ttu-id="2846f-118">前 4 個位元組包含字典項目數 (也就是字典中的相對虛擬位址數目)。</span><span class="sxs-lookup"><span data-stu-id="2846f-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="2846f-119">我們將這個值為*N*。如果設定高位元，項目會依相對虛擬位址的遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="2846f-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>  
  
-   <span data-ttu-id="2846f-120">*N*遵循目錄項目。</span><span class="sxs-lookup"><span data-stu-id="2846f-120">The *N* directory entries follow.</span></span> <span data-ttu-id="2846f-121">每個項目是由兩個 4 位元組區段中的 8 個位元組所組成：</span><span class="sxs-lookup"><span data-stu-id="2846f-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>  
  
    -   <span data-ttu-id="2846f-122">位元組 0-3：RVA；字典的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="2846f-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>  
  
    -   <span data-ttu-id="2846f-123">位元組 4-7：位移；相對於堆積開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="2846f-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>  
  
<a name="Heap"></a>   
## <a name="the-heap"></a><span data-ttu-id="2846f-124">堆積</span><span class="sxs-lookup"><span data-stu-id="2846f-124">The Heap</span></span>  
 <span data-ttu-id="2846f-125">堆積的大小可透過資料流讀取器來計算，計算方式是將目錄大小減去資料流長度，再加 4。</span><span class="sxs-lookup"><span data-stu-id="2846f-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="2846f-126">換句話說：</span><span class="sxs-lookup"><span data-stu-id="2846f-126">In other words:</span></span>  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 <span data-ttu-id="2846f-127">其中目錄大小為 `N * 8`。</span><span class="sxs-lookup"><span data-stu-id="2846f-127">where the directory size is `N * 8`.</span></span>  
  
 <span data-ttu-id="2846f-128">堆積上每個具現化資訊項目的格式為：</span><span class="sxs-lookup"><span data-stu-id="2846f-128">The format for each instantiation information item on the heap is:</span></span>  
  
-   <span data-ttu-id="2846f-129">這個具現化資訊項目的長度 (以位元組為單位)，採用壓縮的 ECMA 中繼資料格式。</span><span class="sxs-lookup"><span data-stu-id="2846f-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="2846f-130">該值不包括這個長度資訊。</span><span class="sxs-lookup"><span data-stu-id="2846f-130">The value excludes this length information.</span></span>  
  
-   <span data-ttu-id="2846f-131">泛型具現化類型數目或*T*，採用壓縮的 ECMA 中繼資料格式。</span><span class="sxs-lookup"><span data-stu-id="2846f-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>  
  
-   <span data-ttu-id="2846f-132">*T*類型，分別表示以 ECMA 類型簽章格式。</span><span class="sxs-lookup"><span data-stu-id="2846f-132">*T* types, each represented in ECMA type signature format.</span></span>  
  
 <span data-ttu-id="2846f-133">包含每個堆積項目的長度可簡化目錄區段的排序，而不影響堆積。</span><span class="sxs-lookup"><span data-stu-id="2846f-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2846f-134">需求</span><span class="sxs-lookup"><span data-stu-id="2846f-134">Requirements</span></span>  
 <span data-ttu-id="2846f-135">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2846f-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2846f-136">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2846f-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2846f-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2846f-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2846f-138">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2846f-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2846f-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2846f-139">See Also</span></span>  
 [<span data-ttu-id="2846f-140">ICorDebugSymbolProvider2 介面</span><span class="sxs-lookup"><span data-stu-id="2846f-140">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="2846f-141">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2846f-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
