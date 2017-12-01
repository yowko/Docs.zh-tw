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
# <a name="memory-mapped-files"></a>記憶體對應檔案
記憶體對應檔案包含檔案在虛擬記憶體中的內容。 這個檔案和記憶體空間之間的對應可讓應用程式，包括多個處理程序，以進行讀取和寫入至記憶體中直接修改檔案。 從開始[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，您可以使用 managed 程式碼至原生 Windows 函式，存取記憶體對應檔案，以相同方式存取記憶體對應檔中所述[Managing Memory-Mapped 檔案中 Win32](http://go.microsoft.com/fwlink/?linkid=180801)。  
  
 有兩種類型的記憶體對應檔：  
  
-   保存記憶體對應檔  
  
     保存的檔案是磁碟上的原始程式檔相關聯的記憶體對應檔案。 最後一個程序完成時使用的檔案，資料會儲存到磁碟上的來源檔案。 這些記憶體對應檔案是適用於處理極大的來源檔案。  
  
-   非保存記憶體對應檔  
  
     非保存的檔案是未在磁碟上的檔案與相關聯的記憶體對應檔案。 最後一個程序完成時使用的檔案，資料會遺失，而且檔案回收進行回收。 這些檔案是適合用來建立共用的記憶體的處理序間通訊 (IPC)。  
  
## <a name="processes-views-and-managing-memory"></a>處理程序、 檢視和管理記憶體  
 記憶體對應檔可以跨多個處理序共用。 處理程序可以使用 建立檔案的處理序所指派的一般名稱對應至相同的記憶體對應檔案。  
  
 若要使用的記憶體對應檔，您必須建立部分或整個記憶體對應檔案的檢視。 您也可以建立多個檢視，以相同的組件的記憶體對應檔，藉此建立並行的記憶體。 兩個檢視，來維持並行，他們必須建立從相同的記憶體對應檔。  
  
 多個檢視也可能需要的檔案是否大於可用的記憶體對應 (32 位元電腦上的 2 GB) 的應用程式的邏輯記憶體空間的大小。  
  
 有兩種檢視： 資料流存取檢視和隨機存取檢視。 將資料流存取檢視表用於循序方式存取檔案。這被建議的非保存的檔案和 IPC。 隨機存取檢視是慣用使用保存的檔案。  
  
 記憶體對應檔案是透過作業系統的記憶體管理員中，存取，以便自動分割成頁數並視需要存取檔案。 您不必自行處理記憶體管理。  
  
 下圖顯示如何在多個處理序可以有多個與重疊檢視相同的記憶體對應檔案，在相同的時間。  
  
 ![顯示檢視，以記憶體 &#45; 對應的檔。] (../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")  
多個和重疊的實的記憶體對應檔的檢視  
  
## <a name="programming-with-memory-mapped-files"></a>使用記憶體對應檔進行程式設計  
 下表提供使用記憶體對應檔的物件和其成員的指南。  
  
|工作|若要使用的屬性或方法|  
|----------|----------------------------------|  
|若要取得<xref:System.IO.MemoryMappedFiles.MemoryMappedFile>物件，表示持續性的記憶體對應檔，從磁碟上的檔案。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> 方法。|  
|若要取得<xref:System.IO.MemoryMappedFiles.MemoryMappedFile>物件，表示非持續性記憶體對應檔 （與磁碟上的檔案沒有關聯）。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> 方法。<br /><br /> -或-<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> 方法。|  
|若要取得<xref:System.IO.MemoryMappedFiles.MemoryMappedFile>物件現有的記憶體對應檔 （保存或非保存）。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> 方法。|  
|若要取得<xref:System.IO.UnmanagedMemoryStream>給記憶體對應檔的循序存取檢視的物件。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> 方法。|  
|若要取得<xref:System.IO.UnmanagedMemoryAccessor>物件隨機存取記憶體對應檢視 fie。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> 方法。|  
|若要取得<xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle>用於與 unmanaged 程式碼的物件。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> 屬性。<br /><br /> -或-<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> 屬性。<br /><br /> -或-<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> 屬性。|  
|若要延遲配置記憶體之前檢視建立 （僅限非保存檔）。<br /><br /> (若要判斷目前的系統分頁大小，請使用<xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType>屬性。)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>方法具有<xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType>值。<br /><br /> -或-<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>具有方法<xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions>列舉型別做為參數。|  
  
### <a name="security"></a>安全性  
 您可以套用的存取權限，當您建立記憶體對應檔案，使用下列方法會採用<xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess>列舉型別做為參數：  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 您可以指定使用開啟現有的記憶體對應檔案的存取權限<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A>方法會採用<xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights>做為參數。  
  
 此外，您可以包含<xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity>物件，其中包含預先定義的存取規則。  
  
 若要將新的或變更的存取規則套用至記憶體對應檔案，使用<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A>方法。 擷取存取或稽核規則從現有的檔案，請使用<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A>方法。  
  
## <a name="examples"></a>範例  
  
### <a name="persisted-memory-mapped-files"></a>保存記憶體對應檔  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A>方法從磁碟上現有的檔案建立記憶體對應檔案。  
  
 下例會建立記憶體對應檢視的極大的檔案部分，及操作的一部分。  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 下列範例會開啟另一個處理序的相同記憶體對應檔。  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>非持續性記憶體對應檔  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>和<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>方法建立記憶體對應檔案，則未對應到磁碟上現有的檔案。  
  
 下列範例包含三個不同的處理序 （主控台應用程式） 的布林值寫入的記憶體對應檔。 發生下列動作順序：  
  
1.  `Process A`建立記憶體對應檔案，並將值寫入它。  
  
2.  `Process B`開啟記憶體對應檔，並將值寫入它。  
  
3.  `Process C`開啟記憶體對應檔，並將值寫入它。  
  
4.  `Process A`讀取並顯示於記憶體對應檔中的值。  
  
5.  之後`Process A`資料庫已使用記憶體對應檔案中，檔案會立即回收記憶體回收。  
  
 若要執行此範例中，執行下列作業：  
  
1.  編譯應用程式，並開啟三個命令提示字元視窗。  
  
2.  在第一個命令提示字元視窗中，執行`Process A`。  
  
3.  在第二個命令提示字元視窗中，執行`Process B`。  
  
4.  返回`Process A`按下 ENTER。  
  
5.  在第三個命令提示字元視窗中，執行`Process C`。  
  
6.  返回`Process A`按下 ENTER。  
  
 輸出`Process A`如下所示：  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **處理序的**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **處理序 B**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **處理序 C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 [檔案和資料流 I-O](../../../docs/standard/io/index.md)
