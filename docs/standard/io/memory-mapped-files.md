---
title: "記憶體對應檔案"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communiation
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2602d431aada7b3e0ee226eed319903492022ae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="memory-mapped-files"></a><span data-ttu-id="8aeb1-102">記憶體對應檔案</span><span class="sxs-lookup"><span data-stu-id="8aeb1-102">Memory-Mapped Files</span></span>
<span data-ttu-id="8aeb1-103">記憶體對應檔案包含檔案在虛擬記憶體中的內容。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="8aeb1-104">這個檔案和記憶體空間之間的對應可讓應用程式，包括多個處理程序，以進行讀取和寫入至記憶體中直接修改檔案。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="8aeb1-105">從開始[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，您可以使用 managed 程式碼至原生 Windows 函式，存取記憶體對應檔案，以相同方式存取記憶體對應檔中所述[Managing Memory-Mapped 檔案中 Win32](http://go.microsoft.com/fwlink/?linkid=180801)。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files in Win32](http://go.microsoft.com/fwlink/?linkid=180801).</span></span>  
  
 <span data-ttu-id="8aeb1-106">有兩種類型的記憶體對應檔：</span><span class="sxs-lookup"><span data-stu-id="8aeb1-106">There are two types of memory-mapped files:</span></span>  
  
-   <span data-ttu-id="8aeb1-107">保存記憶體對應檔</span><span class="sxs-lookup"><span data-stu-id="8aeb1-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="8aeb1-108">保存的檔案是磁碟上的原始程式檔相關聯的記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="8aeb1-109">最後一個程序完成時使用的檔案，資料會儲存到磁碟上的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="8aeb1-110">這些記憶體對應檔案是適用於處理極大的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
-   <span data-ttu-id="8aeb1-111">非保存記憶體對應檔</span><span class="sxs-lookup"><span data-stu-id="8aeb1-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="8aeb1-112">非保存的檔案是未在磁碟上的檔案與相關聯的記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="8aeb1-113">最後一個程序完成時使用的檔案，資料會遺失，而且檔案回收進行回收。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="8aeb1-114">這些檔案是適合用來建立共用的記憶體的處理序間通訊 (IPC)。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="8aeb1-115">處理程序、 檢視和管理記憶體</span><span class="sxs-lookup"><span data-stu-id="8aeb1-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="8aeb1-116">記憶體對應檔可以跨多個處理序共用。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="8aeb1-117">處理程序可以使用 建立檔案的處理序所指派的一般名稱對應至相同的記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="8aeb1-118">若要使用的記憶體對應檔，您必須建立部分或整個記憶體對應檔案的檢視。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="8aeb1-119">您也可以建立多個檢視，以相同的組件的記憶體對應檔，藉此建立並行的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="8aeb1-120">兩個檢視，來維持並行，他們必須建立從相同的記憶體對應檔。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="8aeb1-121">多個檢視也可能需要的檔案是否大於可用的記憶體對應 (32 位元電腦上的 2 GB) 的應用程式的邏輯記憶體空間的大小。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="8aeb1-122">有兩種檢視： 資料流存取檢視和隨機存取檢視。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="8aeb1-123">將資料流存取檢視表用於循序方式存取檔案。這被建議的非保存的檔案和 IPC。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="8aeb1-124">隨機存取檢視是慣用使用保存的檔案。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="8aeb1-125">記憶體對應檔案是透過作業系統的記憶體管理員中，存取，以便自動分割成頁數並視需要存取檔案。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="8aeb1-126">您不必自行處理記憶體管理。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="8aeb1-127">下圖顯示如何在多個處理序可以有多個與重疊檢視相同的記憶體對應檔案，在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>  
  
 <span data-ttu-id="8aeb1-128">![顯示檢視，以記憶體 &#45; 對應的檔。] (../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")</span><span class="sxs-lookup"><span data-stu-id="8aeb1-128">![Shows views to a memory&#45;mapped file.](../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")</span></span>  
<span data-ttu-id="8aeb1-129">多個和重疊的實的記憶體對應檔的檢視</span><span class="sxs-lookup"><span data-stu-id="8aeb1-129">Multiple and overlapped views to a memory-mapped file</span></span>  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="8aeb1-130">使用記憶體對應檔進行程式設計</span><span class="sxs-lookup"><span data-stu-id="8aeb1-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="8aeb1-131">下表提供使用記憶體對應檔的物件和其成員的指南。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="8aeb1-132">工作</span><span class="sxs-lookup"><span data-stu-id="8aeb1-132">Task</span></span>|<span data-ttu-id="8aeb1-133">若要使用的屬性或方法</span><span class="sxs-lookup"><span data-stu-id="8aeb1-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="8aeb1-134">若要取得<xref:System.IO.MemoryMappedFiles.MemoryMappedFile>物件，表示持續性的記憶體對應檔，從磁碟上的檔案。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="8aeb1-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="8aeb1-136">若要取得<xref:System.IO.MemoryMappedFiles.MemoryMappedFile>物件，表示非持續性記憶體對應檔 （與磁碟上的檔案沒有關聯）。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="8aeb1-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="8aeb1-138">-或-</span><span class="sxs-lookup"><span data-stu-id="8aeb1-138">- or -</span></span><br /><br /> <span data-ttu-id="8aeb1-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="8aeb1-140">若要取得<xref:System.IO.MemoryMappedFiles.MemoryMappedFile>物件現有的記憶體對應檔 （保存或非保存）。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="8aeb1-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="8aeb1-142">若要取得<xref:System.IO.UnmanagedMemoryStream>給記憶體對應檔的循序存取檢視的物件。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="8aeb1-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="8aeb1-144">若要取得<xref:System.IO.UnmanagedMemoryAccessor>物件隨機存取記憶體對應檢視 fie。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="8aeb1-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="8aeb1-146">若要取得<xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle>用於與 unmanaged 程式碼的物件。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="8aeb1-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="8aeb1-148">-或-</span><span class="sxs-lookup"><span data-stu-id="8aeb1-148">- or -</span></span><br /><br /> <span data-ttu-id="8aeb1-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="8aeb1-150">-或-</span><span class="sxs-lookup"><span data-stu-id="8aeb1-150">- or -</span></span><br /><br /> <span data-ttu-id="8aeb1-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="8aeb1-152">若要延遲配置記憶體之前檢視建立 （僅限非保存檔）。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="8aeb1-153">(若要判斷目前的系統分頁大小，請使用<xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType>屬性。)</span><span class="sxs-lookup"><span data-stu-id="8aeb1-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="8aeb1-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>方法具有<xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType>值。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="8aeb1-155">-或-</span><span class="sxs-lookup"><span data-stu-id="8aeb1-155">- or -</span></span><br /><br /> <span data-ttu-id="8aeb1-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>具有方法<xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions>列舉型別做為參數。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="8aeb1-157">安全性</span><span class="sxs-lookup"><span data-stu-id="8aeb1-157">Security</span></span>  
 <span data-ttu-id="8aeb1-158">您可以套用的存取權限，當您建立記憶體對應檔案，使用下列方法會採用<xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess>列舉型別做為參數：</span><span class="sxs-lookup"><span data-stu-id="8aeb1-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="8aeb1-159">您可以指定使用開啟現有的記憶體對應檔案的存取權限<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A>方法會採用<xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights>做為參數。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="8aeb1-160">此外，您可以包含<xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity>物件，其中包含預先定義的存取規則。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="8aeb1-161">若要將新的或變更的存取規則套用至記憶體對應檔案，使用<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="8aeb1-162">擷取存取或稽核規則從現有的檔案，請使用<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8aeb1-163">範例</span><span class="sxs-lookup"><span data-stu-id="8aeb1-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="8aeb1-164">保存記憶體對應檔</span><span class="sxs-lookup"><span data-stu-id="8aeb1-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="8aeb1-165"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A>方法從磁碟上現有的檔案建立記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="8aeb1-166">下例會建立記憶體對應檢視的極大的檔案部分，及操作的一部分。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 <span data-ttu-id="8aeb1-167">下列範例會開啟另一個處理序的相同記憶體對應檔。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="8aeb1-168">非持續性記憶體對應檔</span><span class="sxs-lookup"><span data-stu-id="8aeb1-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="8aeb1-169"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>和<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>方法建立記憶體對應檔案，則未對應到磁碟上現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="8aeb1-170">下列範例包含三個不同的處理序 （主控台應用程式） 的布林值寫入的記憶體對應檔。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="8aeb1-171">發生下列動作順序：</span><span class="sxs-lookup"><span data-stu-id="8aeb1-171">The following sequence of actions occur:</span></span>  
  
1.  <span data-ttu-id="8aeb1-172">`Process A`建立記憶體對應檔案，並將值寫入它。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-172">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2.  <span data-ttu-id="8aeb1-173">`Process B`開啟記憶體對應檔，並將值寫入它。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-173">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3.  <span data-ttu-id="8aeb1-174">`Process C`開啟記憶體對應檔，並將值寫入它。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-174">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4.  <span data-ttu-id="8aeb1-175">`Process A`讀取並顯示於記憶體對應檔中的值。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-175">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5.  <span data-ttu-id="8aeb1-176">之後`Process A`資料庫已使用記憶體對應檔案中，檔案會立即回收記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="8aeb1-177">若要執行此範例中，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="8aeb1-177">To run this example, do the following:</span></span>  
  
1.  <span data-ttu-id="8aeb1-178">編譯應用程式，並開啟三個命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2.  <span data-ttu-id="8aeb1-179">在第一個命令提示字元視窗中，執行`Process A`。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3.  <span data-ttu-id="8aeb1-180">在第二個命令提示字元視窗中，執行`Process B`。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4.  <span data-ttu-id="8aeb1-181">返回`Process A`按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-181">Return to `Process A` and press ENTER.</span></span>  
  
5.  <span data-ttu-id="8aeb1-182">在第三個命令提示字元視窗中，執行`Process C`。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6.  <span data-ttu-id="8aeb1-183">返回`Process A`按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="8aeb1-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="8aeb1-184">輸出`Process A`如下所示：</span><span class="sxs-lookup"><span data-stu-id="8aeb1-184">The output of `Process A` is as follows:</span></span>  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="8aeb1-185">**處理序的**</span><span class="sxs-lookup"><span data-stu-id="8aeb1-185">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="8aeb1-186">**處理序 B**</span><span class="sxs-lookup"><span data-stu-id="8aeb1-186">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="8aeb1-187">**處理序 C**</span><span class="sxs-lookup"><span data-stu-id="8aeb1-187">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8aeb1-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8aeb1-188">See Also</span></span>  
 [<span data-ttu-id="8aeb1-189">檔案和資料流 I-O</span><span class="sxs-lookup"><span data-stu-id="8aeb1-189">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
