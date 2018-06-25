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
ms.openlocfilehash: 1cf2d7f36dbfffe1c86e32eec5137840837612f4
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208146"
---
# <a name="memory-mapped-files"></a>記憶體對應檔案
記憶體對應檔案包含檔案在虛擬記憶體中的內容。 檔案和記憶體空間之間的這個對應可讓應用程式 (包括多個處理序) 透過直接讀取和寫入記憶體來修改檔案。 從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，您可以利用與原生 Windows 功能存取記憶體對應檔案相同的方法，使用 受控碼來存取記憶體對應檔案，如[管理記憶體對應檔案](https://msdn.microsoft.com/library/ms810613.aspx) \(英文\) 所述。  
  
 記憶體對應檔案的類型有兩種：  
  
-   持續性記憶體對應檔案  
  
     持續性檔案是與磁碟上之原始程式檔相關聯的記憶體對應檔案。 當最後一個處理序完成檔案處理時，資料就會儲存到磁碟上的原始程式檔。 這些記憶體對應檔案適合處理極大的原始程式檔。  
  
-   非持續性記憶體對應檔案  
  
     非持續性檔案是與磁碟上的檔案沒有關聯的記憶體對應檔案。 當最後一個處理序完成檔案處理時，資料就會遺失，而且該檔案會由記憶體回收進行回收。 這些檔案適合為處理序間通訊 (IPC) 建立共用記憶體。  
  
## <a name="processes-views-and-managing-memory"></a>處理序、檢視和管理記憶體  
 記憶體對應檔案可以跨多個處理序共用。 處理序可以使用建立檔案之處理序所指派的一般名稱，對應至相同的記憶體對應檔案。  
  
 若要處理記憶體對應檔案，您必須建立整個或部分記憶體對應檔案的檢視。 您也可以對記憶體對應檔案的相同部分建立多個檢視，藉此建立並行記憶體。 若要讓兩個檢視維持並行，必須從相同的記憶體對應檔案建立這兩個檢視。  
  
 如果檔案大於可用於記憶體對應 (在 32 位元電腦上為 2 GB) 的應用程式邏輯記憶體空間大小，也可能需要多個檢視。  
  
 檢視有兩種：資料流存取檢視和隨機存取檢視。 將資料流存取檢視用於循序存取檔案；建議將此種方式用於非持續性檔案和 IPC。 若要處理持續性檔案，建議使用隨機存取檢視。  
  
 記憶體對應檔案是透過作業系統的記憶體管理員存取的，因此檔案會被自動分割成多頁並視需要進行存取。 您不必自行處理記憶體管理。  
  
 下圖顯示多個處理序如何同時對相同的記憶體對應檔案擁有多個重疊的檢視。  
  
 ![將檢視顯示為記憶體對應檔案。](../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")  
對記憶體對應檔案的多個重疊檢視  
  
## <a name="programming-with-memory-mapped-files"></a>使用記憶體對應檔案進行程式設計  
 下表提供使用記憶體對應檔案物件及其成員的指南。  
  
|工作|要使用的方法或屬性|  
|----------|----------------------------------|  
|從磁碟上的檔案取得表示持續性記憶體對應檔案的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 物件。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> 方法。|  
|取得表示非持續性記憶體對應檔案 (與磁碟上的檔案沒有關聯) 的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 物件。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> 方法。<br /><br /> -或-<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> 方法。|  
|取得現有記憶體對應檔案 (持續性或非持續性) 的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 物件。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> 方法。|  
|針對記憶體對應檔案，取得循序存取檢視的 <xref:System.IO.UnmanagedMemoryStream> 物件。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> 方法。|  
|針對記憶體對應檔案，取得隨機存取檢視的 <xref:System.IO.UnmanagedMemoryAccessor> 物件。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> 方法。|  
|取得搭配非受控程式碼 使用的 <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> 物件。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> 屬性。<br /><br /> -或-<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> 屬性。<br /><br /> -或-<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> 屬性。|  
|延遲配置記憶體，直到建立檢視 (僅限非持續性檔案) 為止 <br /><br /> (若要判斷目前的系統頁面大小，請使用 <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> 屬性)。|具有 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> 值的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> 方法。<br /><br /> -或-<br /><br /> 將 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> 列舉當作參數的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> 方法。|  
  
### <a name="security"></a>安全性  
 使用下列採用 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> 列舉作為參數的方法建立記憶體對應檔案時，您可以套用存取權限：  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 您可以使用採用 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> 作為參數的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> 方法指定存取權限，來開啟現有的記憶體對應檔案。  
  
 此外，您還可以加入內含預先定義之存取規則的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> 物件。  
  
 若要將新的或變更的存取規則套用至記憶體對應檔案，請使用 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> 方法。 若要從現有的檔案擷取存取或稽核規則，請使用 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> 方法。  
  
## <a name="examples"></a>範例  
  
### <a name="persisted-memory-mapped-files"></a>持續性記憶體對應檔案  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> 方法會從磁碟上現有的檔案建立記憶體對應檔案。  
  
 下列範例會針對極大檔案的一部分建立記憶體對應檢視，及操作其中的一部分。  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 下列範例會為另一個處理序開啟相同的記憶體對應檔案。  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>非持續性記憶體對應檔案  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> 和 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> 方法會建立非對應至磁碟上現有檔案的記憶體對應檔案。  
  
 下列範例包含三個不同的處理序 (主控台應用程式)，這些處理序會將布林值寫入記憶體對應檔案。 發生下列順序的動作：  
  
1.  `Process A` 會建立記憶體對應檔案，並在其中寫入值。  
  
2.  `Process B` 會開啟記憶體對應檔案，並在其中寫入值。  
  
3.  `Process C` 會開啟記憶體對應檔案，並在其中寫入值。  
  
4.  `Process A` 會讀取並顯示記憶體對應檔案中的值。  
  
5.  使用記憶體對應檔案完成 `Process A` 之後，檔案會立即由記憶體回收進行回收。  
  
 若要執行此範例，請執行下列動作：  
  
1.  編譯應用程式，並開啟三個 [命令提示字元] 視窗。  
  
2.  在第一個 [命令提示字元] 視窗中，執行 `Process A`。  
  
3.  在第二個 [命令提示字元] 視窗中，執行 `Process B`。  
  
4.  返回 `Process A`，然後按 ENTER。  
  
5.  在第三個 [命令提示字元] 視窗中，執行 `Process C`。  
  
6.  返回 `Process A`，然後按 ENTER。  
  
 `Process A` 的輸出如下：  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **Process A**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **Process B**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **Process C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 [檔案和資料流 I/O](../../../docs/standard/io/index.md)
