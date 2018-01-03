---
title: "ICorDebugSymbolProvider 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63823c535ad4d036dd5d539c8fe5381d350ccbe5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="ea4ec-102">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="ea4ec-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="ea4ec-103">提供可用來擷取偵錯符號資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea4ec-104">方法</span><span class="sxs-lookup"><span data-stu-id="ea4ec-104">Methods</span></span>  
  
|<span data-ttu-id="ea4ec-105">方法</span><span class="sxs-lookup"><span data-stu-id="ea4ec-105">Method</span></span>|<span data-ttu-id="ea4ec-106">描述</span><span class="sxs-lookup"><span data-stu-id="ea4ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea4ec-107">GetAssemblyImageBytes 方法</span><span class="sxs-lookup"><span data-stu-id="ea4ec-107">GetAssemblyImageBytes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="ea4ec-108">如果合併組件中有相對虛擬位址 (RVA)，則會從合併組件讀取資料。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="ea4ec-109">GetAssemblyImageMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="ea4ec-109">GetAssemblyImageMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="ea4ec-110">從合併組件傳回中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="ea4ec-111">GetCodeRange 方法</span><span class="sxs-lookup"><span data-stu-id="ea4ec-111">GetCodeRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="ea4ec-112">提供方法中的相對虛擬位址 (RVA)，以取得方法起始位址和大小。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="ea4ec-113">GetInstanceFieldSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="ea4ec-113">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="ea4ec-114">取得對應 TypeSpec 簽章的執行個體欄位符號。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="ea4ec-115">GetMergedAssemblyRecords 方法</span><span class="sxs-lookup"><span data-stu-id="ea4ec-115">GetMergedAssemblyRecords Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="ea4ec-116">取得所有合併組件的符號記錄。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="ea4ec-117">GetMethodLocalSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="ea4ec-117">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="ea4ec-118">提供方法的相對虛擬位址 (RVA)，取得該方法的本機符號。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="ea4ec-119">GetMethodParameterSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="ea4ec-119">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="ea4ec-120">提供方法的相對虛擬位址 (RVA)，取得該方法的參數符號。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="ea4ec-121">GetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="ea4ec-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="ea4ec-122">傳回方法屬性的相關資訊，例如方法的中繼資料語彙基元，以及其泛型參數的相關資訊 (假設該方法中有相對虛擬位址 (RVA))。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="ea4ec-123">GetObjectSize 方法</span><span class="sxs-lookup"><span data-stu-id="ea4ec-123">GetObjectSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="ea4ec-124">傳回根據某物件之 typespec 簽章的該物件大小。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="ea4ec-125">GetStaticFieldSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="ea4ec-125">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="ea4ec-126">取得對應至 TypeSpec 簽章的靜態欄位符號。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="ea4ec-127">GetTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="ea4ec-127">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="ea4ec-128">根據 vtable 中指定的相對虛擬位址 (RVA)，傳回類型之屬性的相關資訊，例如其泛型參數的簽章數目。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea4ec-129">備註</span><span class="sxs-lookup"><span data-stu-id="ea4ec-129">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea4ec-130">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="ea4ec-131">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea4ec-132">需求</span><span class="sxs-lookup"><span data-stu-id="ea4ec-132">Requirements</span></span>  
 <span data-ttu-id="ea4ec-133">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea4ec-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea4ec-134">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea4ec-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea4ec-135">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea4ec-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea4ec-136">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea4ec-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea4ec-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea4ec-137">See Also</span></span>  
 [<span data-ttu-id="ea4ec-138">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ea4ec-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ea4ec-139">偵錯</span><span class="sxs-lookup"><span data-stu-id="ea4ec-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
