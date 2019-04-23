---
title: 記憶體對應檔案
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7bda02e1862740e6a6328835367a6a5e9929033
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328305"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="ff796-102">記憶體對應檔案</span><span class="sxs-lookup"><span data-stu-id="ff796-102">Memory-Mapped Files</span></span>
<span data-ttu-id="ff796-103">記憶體對應檔案包含檔案在虛擬記憶體中的內容。</span><span class="sxs-lookup"><span data-stu-id="ff796-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="ff796-104">檔案和記憶體空間之間的這個對應可讓應用程式 (包括多個處理序) 透過直接讀取和寫入記憶體來修改檔案。</span><span class="sxs-lookup"><span data-stu-id="ff796-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="ff796-105">從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，您可以利用與原生 Windows 功能存取記憶體對應檔案相同的方法，使用 受控碼來存取記憶體對應檔案，如[管理記憶體對應檔案](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)) \(英文\) 所述。</span><span class="sxs-lookup"><span data-stu-id="ff796-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="ff796-106">記憶體對應檔案的類型有兩種：</span><span class="sxs-lookup"><span data-stu-id="ff796-106">There are two types of memory-mapped files:</span></span>  
  
-   <span data-ttu-id="ff796-107">持續性記憶體對應檔案</span><span class="sxs-lookup"><span data-stu-id="ff796-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="ff796-108">持續性檔案是與磁碟上之原始程式檔相關聯的記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="ff796-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="ff796-109">當最後一個處理序完成檔案處理時，資料就會儲存到磁碟上的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="ff796-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="ff796-110">這些記憶體對應檔案適合處理極大的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="ff796-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
-   <span data-ttu-id="ff796-111">非持續性記憶體對應檔案</span><span class="sxs-lookup"><span data-stu-id="ff796-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="ff796-112">非持續性檔案是與磁碟上的檔案沒有關聯的記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="ff796-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="ff796-113">當最後一個處理序完成檔案處理時，資料就會遺失，而且該檔案會由記憶體回收進行回收。</span><span class="sxs-lookup"><span data-stu-id="ff796-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="ff796-114">這些檔案適合為處理序間通訊 (IPC) 建立共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="ff796-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="ff796-115">處理序、檢視和管理記憶體</span><span class="sxs-lookup"><span data-stu-id="ff796-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="ff796-116">記憶體對應檔案可以跨多個處理序共用。</span><span class="sxs-lookup"><span data-stu-id="ff796-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="ff796-117">處理序可以使用建立檔案之處理序所指派的一般名稱，對應至相同的記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="ff796-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="ff796-118">若要處理記憶體對應檔案，您必須建立整個或部分記憶體對應檔案的檢視。</span><span class="sxs-lookup"><span data-stu-id="ff796-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="ff796-119">您也可以對記憶體對應檔案的相同部分建立多個檢視，藉此建立並行記憶體。</span><span class="sxs-lookup"><span data-stu-id="ff796-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="ff796-120">若要讓兩個檢視維持並行，必須從相同的記憶體對應檔案建立這兩個檢視。</span><span class="sxs-lookup"><span data-stu-id="ff796-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="ff796-121">如果檔案大於可用於記憶體對應 (在 32 位元電腦上為 2 GB) 的應用程式邏輯記憶體空間大小，也可能需要多個檢視。</span><span class="sxs-lookup"><span data-stu-id="ff796-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="ff796-122">檢視有兩種：資料流存取檢視和隨機存取檢視。</span><span class="sxs-lookup"><span data-stu-id="ff796-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="ff796-123">將資料流存取檢視用於循序存取檔案；建議將此種方式用於非持續性檔案和 IPC。</span><span class="sxs-lookup"><span data-stu-id="ff796-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="ff796-124">若要處理持續性檔案，建議使用隨機存取檢視。</span><span class="sxs-lookup"><span data-stu-id="ff796-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="ff796-125">記憶體對應檔案是透過作業系統的記憶體管理員存取的，因此檔案會被自動分割成多頁並視需要進行存取。</span><span class="sxs-lookup"><span data-stu-id="ff796-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="ff796-126">您不必自行處理記憶體管理。</span><span class="sxs-lookup"><span data-stu-id="ff796-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="ff796-127">下圖顯示多個處理序如何同時對相同的記憶體對應檔案擁有多個重疊的檢視。</span><span class="sxs-lookup"><span data-stu-id="ff796-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="ff796-128">下圖顯示對記憶體對應檔案的多個重疊檢視：</span><span class="sxs-lookup"><span data-stu-id="ff796-128">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![將檢視顯示為記憶體對應檔案的螢幕擷取畫面。](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="ff796-130">使用記憶體對應檔案進行程式設計</span><span class="sxs-lookup"><span data-stu-id="ff796-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="ff796-131">下表提供使用記憶體對應檔案物件及其成員的指南。</span><span class="sxs-lookup"><span data-stu-id="ff796-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="ff796-132">工作</span><span class="sxs-lookup"><span data-stu-id="ff796-132">Task</span></span>|<span data-ttu-id="ff796-133">要使用的方法或屬性</span><span class="sxs-lookup"><span data-stu-id="ff796-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="ff796-134">從磁碟上的檔案取得表示持續性記憶體對應檔案的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 物件。</span><span class="sxs-lookup"><span data-stu-id="ff796-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> <span data-ttu-id="ff796-135">方法。</span><span class="sxs-lookup"><span data-stu-id="ff796-135">method.</span></span>|  
|<span data-ttu-id="ff796-136">取得表示非持續性記憶體對應檔案 (與磁碟上的檔案沒有關聯) 的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 物件。</span><span class="sxs-lookup"><span data-stu-id="ff796-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> <span data-ttu-id="ff796-137">方法。</span><span class="sxs-lookup"><span data-stu-id="ff796-137">method.</span></span><br /><br /> <span data-ttu-id="ff796-138">-或-</span><span class="sxs-lookup"><span data-stu-id="ff796-138">- or -</span></span><br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> <span data-ttu-id="ff796-139">方法。</span><span class="sxs-lookup"><span data-stu-id="ff796-139">method.</span></span>|  
|<span data-ttu-id="ff796-140">取得現有記憶體對應檔案 (持續性或非持續性) 的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 物件。</span><span class="sxs-lookup"><span data-stu-id="ff796-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> <span data-ttu-id="ff796-141">方法。</span><span class="sxs-lookup"><span data-stu-id="ff796-141">method.</span></span>|  
|<span data-ttu-id="ff796-142">針對記憶體對應檔案，取得循序存取檢視的 <xref:System.IO.UnmanagedMemoryStream> 物件。</span><span class="sxs-lookup"><span data-stu-id="ff796-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> <span data-ttu-id="ff796-143">方法。</span><span class="sxs-lookup"><span data-stu-id="ff796-143">method.</span></span>|  
|<span data-ttu-id="ff796-144">針對記憶體對應檔案，取得隨機存取檢視的 <xref:System.IO.UnmanagedMemoryAccessor> 物件。</span><span class="sxs-lookup"><span data-stu-id="ff796-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> <span data-ttu-id="ff796-145">方法。</span><span class="sxs-lookup"><span data-stu-id="ff796-145">method.</span></span>|  
|<span data-ttu-id="ff796-146">取得搭配非受控程式碼 使用的 <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> 物件。</span><span class="sxs-lookup"><span data-stu-id="ff796-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> <span data-ttu-id="ff796-147">屬性。</span><span class="sxs-lookup"><span data-stu-id="ff796-147">property.</span></span><br /><br /> <span data-ttu-id="ff796-148">-或-</span><span class="sxs-lookup"><span data-stu-id="ff796-148">- or -</span></span><br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> <span data-ttu-id="ff796-149">屬性。</span><span class="sxs-lookup"><span data-stu-id="ff796-149">property.</span></span><br /><br /> <span data-ttu-id="ff796-150">-或-</span><span class="sxs-lookup"><span data-stu-id="ff796-150">- or -</span></span><br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> <span data-ttu-id="ff796-151">屬性。</span><span class="sxs-lookup"><span data-stu-id="ff796-151">property.</span></span>|  
|<span data-ttu-id="ff796-152">延遲配置記憶體，直到建立檢視 (僅限非持續性檔案) 為止 </span><span class="sxs-lookup"><span data-stu-id="ff796-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="ff796-153">(若要判斷目前的系統頁面大小，請使用 <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> 屬性)。</span><span class="sxs-lookup"><span data-stu-id="ff796-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> <span data-ttu-id="ff796-154">方法，具有 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> 值。</span><span class="sxs-lookup"><span data-stu-id="ff796-154">method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="ff796-155">-或-</span><span class="sxs-lookup"><span data-stu-id="ff796-155">- or -</span></span><br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> <span data-ttu-id="ff796-156">方法，具有 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> 列舉作為參數。</span><span class="sxs-lookup"><span data-stu-id="ff796-156">methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="ff796-157">安全性</span><span class="sxs-lookup"><span data-stu-id="ff796-157">Security</span></span>  
 <span data-ttu-id="ff796-158">使用下列採用 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> 列舉作為參數的方法建立記憶體對應檔案時，您可以套用存取權限：</span><span class="sxs-lookup"><span data-stu-id="ff796-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="ff796-159">您可以使用採用 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> 作為參數的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> 方法指定存取權限，來開啟現有的記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="ff796-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="ff796-160">此外，您還可以加入內含預先定義之存取規則的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> 物件。</span><span class="sxs-lookup"><span data-stu-id="ff796-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="ff796-161">若要將新的或變更的存取規則套用至記憶體對應檔案，請使用 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ff796-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="ff796-162">若要從現有的檔案擷取存取或稽核規則，請使用 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ff796-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ff796-163">範例</span><span class="sxs-lookup"><span data-stu-id="ff796-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="ff796-164">持續性記憶體對應檔案</span><span class="sxs-lookup"><span data-stu-id="ff796-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="ff796-165"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> 方法會從磁碟上現有的檔案建立記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="ff796-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="ff796-166">下列範例會針對極大檔案的一部分建立記憶體對應檢視，及操作其中的一部分。</span><span class="sxs-lookup"><span data-stu-id="ff796-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 <span data-ttu-id="ff796-167">下列範例會為另一個處理序開啟相同的記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="ff796-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="ff796-168">非持續性記憶體對應檔案</span><span class="sxs-lookup"><span data-stu-id="ff796-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="ff796-169"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> 和 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> 方法會建立非對應至磁碟上現有檔案的記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="ff796-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="ff796-170">下列範例包含三個不同的處理序 (主控台應用程式)，這些處理序會將布林值寫入記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="ff796-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="ff796-171">發生下列順序的動作：</span><span class="sxs-lookup"><span data-stu-id="ff796-171">The following sequence of actions occur:</span></span>  
  
1. `Process A` <span data-ttu-id="ff796-172">會建立記憶體對應檔案，並在其中寫入值。</span><span class="sxs-lookup"><span data-stu-id="ff796-172">creates the memory-mapped file and writes a value to it.</span></span>  
  
2. `Process B` <span data-ttu-id="ff796-173">會開啟記憶體對應檔案，並在其中寫入值。</span><span class="sxs-lookup"><span data-stu-id="ff796-173">opens the memory-mapped file and writes a value to it.</span></span>  
  
3. `Process C` <span data-ttu-id="ff796-174">會開啟記憶體對應檔案，並在其中寫入值。</span><span class="sxs-lookup"><span data-stu-id="ff796-174">opens the memory-mapped file and writes a value to it.</span></span>  
  
4. `Process A` <span data-ttu-id="ff796-175">會讀取並顯示記憶體對應檔案中的值。</span><span class="sxs-lookup"><span data-stu-id="ff796-175">reads and displays the values from the memory-mapped file.</span></span>  
  
5. <span data-ttu-id="ff796-176">使用記憶體對應檔案完成 `Process A` 之後，檔案會立即由記憶體回收進行回收。</span><span class="sxs-lookup"><span data-stu-id="ff796-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="ff796-177">若要執行此範例，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ff796-177">To run this example, do the following:</span></span>  
  
1. <span data-ttu-id="ff796-178">編譯應用程式，並開啟三個 [命令提示字元] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ff796-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2. <span data-ttu-id="ff796-179">在第一個 [命令提示字元] 視窗中，執行 `Process A`。</span><span class="sxs-lookup"><span data-stu-id="ff796-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3. <span data-ttu-id="ff796-180">在第二個 [命令提示字元] 視窗中，執行 `Process B`。</span><span class="sxs-lookup"><span data-stu-id="ff796-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4. <span data-ttu-id="ff796-181">返回 `Process A`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="ff796-181">Return to `Process A` and press ENTER.</span></span>  
  
5. <span data-ttu-id="ff796-182">在第三個 [命令提示字元] 視窗中，執行 `Process C`。</span><span class="sxs-lookup"><span data-stu-id="ff796-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6. <span data-ttu-id="ff796-183">返回 `Process A`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="ff796-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="ff796-184">`Process A` 的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="ff796-184">The output of `Process A` is as follows:</span></span>  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **<span data-ttu-id="ff796-185">Process A</span><span class="sxs-lookup"><span data-stu-id="ff796-185">Process A</span></span>**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **<span data-ttu-id="ff796-186">Process B</span><span class="sxs-lookup"><span data-stu-id="ff796-186">Process B</span></span>**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **<span data-ttu-id="ff796-187">Process C</span><span class="sxs-lookup"><span data-stu-id="ff796-187">Process C</span></span>**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ff796-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff796-188">See also</span></span>

- [<span data-ttu-id="ff796-189">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="ff796-189">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
