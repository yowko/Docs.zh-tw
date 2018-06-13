---
title: 中繼資料介面
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a704d531b1c49ffe653009e0e90f33b7a126e91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450995"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="17cc3-102">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-102">Metadata Interfaces</span></span>
<span data-ttu-id="17cc3-103">本節描述 Unmanaged 介面，這會提供您由 .NET Framework 類型、方法、欄位等所公開之中繼資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="17cc3-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17cc3-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="17cc3-104">In This Section</span></span>  
 [<span data-ttu-id="17cc3-105">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-105">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 <span data-ttu-id="17cc3-106">提供動態程式碼編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="17cc3-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="17cc3-107">IHostFilter 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-107">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 <span data-ttu-id="17cc3-108">提供執行階段主機標記處理中的中繼資料語彙基元的方法。</span><span class="sxs-lookup"><span data-stu-id="17cc3-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="17cc3-109">IMapToken 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-109">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 <span data-ttu-id="17cc3-110">提供匯入及發出中繼資料簽章間的對應功能。</span><span class="sxs-lookup"><span data-stu-id="17cc3-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="17cc3-111">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-111">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 <span data-ttu-id="17cc3-112">提供方法，以便支援 Common Language Runtime (CLR) 解析及消耗資源時所用的自我描述模型。</span><span class="sxs-lookup"><span data-stu-id="17cc3-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="17cc3-113">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 <span data-ttu-id="17cc3-114">提供存取及檢查組件資訊清單內容的方法。</span><span class="sxs-lookup"><span data-stu-id="17cc3-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="17cc3-115">IMetaDataConverter 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 <span data-ttu-id="17cc3-116">提供將類型程式庫對應至它們的中繼資料簽章，以及從一個轉換到另一個的方法。</span><span class="sxs-lookup"><span data-stu-id="17cc3-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="17cc3-117">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-117">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 <span data-ttu-id="17cc3-118">`IMetaDataDispenser` 已經過時。</span><span class="sxs-lookup"><span data-stu-id="17cc3-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="17cc3-119">請改用 `IMetaDataDispenserEx`。</span><span class="sxs-lookup"><span data-stu-id="17cc3-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="17cc3-120">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 <span data-ttu-id="17cc3-121">提供方法，以對應建立或修改中繼資料的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="17cc3-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="17cc3-122">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 <span data-ttu-id="17cc3-123">提供方法來建立、 修改和儲存與目前定義範圍相關的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="17cc3-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="17cc3-124">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-124">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 <span data-ttu-id="17cc3-125">提供方法來定義及修改方法的中繼資料簽章和建構函式類型的參數 <xref:System.Type?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="17cc3-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="17cc3-126">IMetaDataError 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-126">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 <span data-ttu-id="17cc3-127">提供回呼機制，以在解析組件的中繼資料簽章期間報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="17cc3-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="17cc3-128">IMetaDataFilter 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-128">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 <span data-ttu-id="17cc3-129">提供標記和篩選中繼資料語彙基元的方法，以避免重複已採取的動作。</span><span class="sxs-lookup"><span data-stu-id="17cc3-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="17cc3-130">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 <span data-ttu-id="17cc3-131">提供從其他組件匯入及管理類型的方法。</span><span class="sxs-lookup"><span data-stu-id="17cc3-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="17cc3-132">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-132">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 <span data-ttu-id="17cc3-133">擴充 `IMetaDataImport` 以提供使用泛用類型的功能。</span><span class="sxs-lookup"><span data-stu-id="17cc3-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="17cc3-134">IMetaDataInfo 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-134">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 <span data-ttu-id="17cc3-135">提供方法，以取得關於將中繼資料從磁碟上檔案對應到記憶體的資訊。</span><span class="sxs-lookup"><span data-stu-id="17cc3-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="17cc3-136">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-136">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 <span data-ttu-id="17cc3-137">提供儲存和擷取資料表中的中繼資料資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="17cc3-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="17cc3-138">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-138">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 <span data-ttu-id="17cc3-139">擴充 `IMetaDataTables` 以包含處理中繼資料資料流的方法。</span><span class="sxs-lookup"><span data-stu-id="17cc3-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="17cc3-140">IMetaDataValidate 介面</span><span class="sxs-lookup"><span data-stu-id="17cc3-140">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 <span data-ttu-id="17cc3-141">提供驗證中繼資料簽章的方法。</span><span class="sxs-lookup"><span data-stu-id="17cc3-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="17cc3-142">相關章節</span><span class="sxs-lookup"><span data-stu-id="17cc3-142">Related Sections</span></span>  
 [<span data-ttu-id="17cc3-143">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="17cc3-143">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [<span data-ttu-id="17cc3-144">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="17cc3-144">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [<span data-ttu-id="17cc3-145">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="17cc3-145">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [<span data-ttu-id="17cc3-146">中繼資料等位</span><span class="sxs-lookup"><span data-stu-id="17cc3-146">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
