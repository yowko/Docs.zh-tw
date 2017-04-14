---
title: "記憶體對應檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "處理序間通訊"
  - "記憶體對應檔案"
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
caps.latest.revision: 24
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 24
---
# 記憶體對應檔案
記憶體對應檔案包含檔案在虛擬記憶體中的內容。  這個對應介於檔案與記憶體空間之間，可以讓包含多個處理序的應用程式，直接對記憶體進行讀取和寫入來修改檔案。  從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，您可以使用如 MSDN Library 中的[在 Win32 中管理記憶體對應檔案](http://go.microsoft.com/fwlink/?linkid=180801) 所述和使用原生 Windows 功能存取記憶體對應檔案一樣的方法利用 Managed 程式碼來存取記憶體對應檔案。  
  
 有兩種類型的記憶體對應檔案：  
  
-   保存的記憶體對應檔案  
  
     保存檔是與磁碟上之原始程式檔關聯的記憶體對應檔案。  最後一個處理序處理完檔案時，資料會儲存到磁碟上的原始程式檔。  這些記憶體對應檔案適合用來處理極大的原始程式檔。  
  
-   非保存的記憶體對應檔案  
  
     非保存檔是未與磁碟上之原始程式檔關聯的記憶體對應檔案。  最後一個處理序處理完檔案時，資料會遺失且記憶體回收會收回檔案。  這些檔案適合用來建立處理序間通訊 \(IPC\) 的共用記憶體。  
  
## 處理、檢視和管理記憶體  
 記憶體對應檔案可以供多個處理序共用。  處理序可以利用當初建立記憶體對應檔案的處理序所指派的一般名稱，來對應至相同的記憶體對應檔案。  
  
 若要使用記憶體對應檔案，您必須對整個或部分記憶體對應檔案建立檢視。  您也可以對記憶體對應檔案的相同部分建立多個檢視，從而建立並行記憶體。  若要讓兩個檢視保持並行，這兩個檢視必須建立自相同的記憶體對應檔案。  
  
 如果檔案大於應用程式用於記憶體對應的邏輯記憶體空間大小 \(在 32 位元電腦上為 2 GB\)，則也可能需要使用多個檢視。  
  
 有兩種檢視：資料流存取檢視和隨機存取檢視。  資料流存取檢視會對檔案進行循序存取，對於非保存檔案和 IPC 建議使用這個檢視。  若要使用保存檔案，則建議使用隨機存取檢視。  
  
 記憶體對應檔案是透過作業系統的記憶體管理員受到存取，所以檔案會自動分割成多個分頁，並視需要受到存取。  您不需要自己親手管理記憶體。  
  
 下圖顯示多個處理序如何才能同時對同一個記憶體對應檔案擁有多個且重疊的檢視。  
  
 ![顯示記憶體對應檔的檢視。](../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")  
記憶體對應檔案的多個且重疊的檢視。  
  
## 使用記憶體對應檔案進行程式設計  
 下表提供記憶體對應檔案物件和其成員的使用指南。  
  
|工作|要使用的方法或屬性|  
|--------|---------------|  
|取得 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 物件，該物件表示磁碟上之檔案的保存記憶體對應檔案。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=fullName> 方法呼叫的。|  
|取得 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 物件，該物件表示非保存記憶體對應檔案 \(與磁碟上的檔案沒有關聯\)。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=fullName> 方法呼叫的。<br /><br /> \-或\-<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=fullName> 方法呼叫的。|  
|取得現有記憶體對應檔案 \(保存或非保存\) 的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 物件。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=fullName> 方法呼叫的。|  
|取得 <xref:System.IO.UnmanagedMemoryStream> 物件以對記憶體對應檔案進行循序存取檢視。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=fullName> 方法呼叫的。|  
|取得 <xref:System.IO.UnmanagedMemoryAccessor> 物件以對記憶體對應檔案進行隨機存取檢視。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=fullName> 方法呼叫的。|  
|取得 <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> 物件以使用 Unmanaged 程式碼。|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=fullName> 屬性。<br /><br /> \-或\-<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=fullName> 屬性。<br /><br /> \-或\-<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=fullName> 屬性。|  
|將記憶體配置延到建立檢視時才進行 \(僅限非保存檔案\)。<br /><br /> \(若要決定目前系統頁面大小，請使用 <xref:System.Environment.SystemPageSize%2A?displayProperty=fullName> 屬性。\)|具有 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions?displayProperty=fullName> 值的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> 方法。<br /><br /> \-或\-<br /><br /> 以 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> 列舉做為參數的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> 方法。|  
  
### 安全性  
 您可以在建立記憶體對應檔案時套用存取權，方法是使用下列以 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> 列舉做為參數的方法：  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=fullName>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=fullName>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=fullName>  
  
 您可以指定開啟現有記憶體對應檔案的存取權，方法是使用以 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> 做為參數的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> 方法。  
  
 此外，您可以納入包含預先定義之存取規則的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> 物件。  
  
 若要將新的或變更的存取規則套用至記憶體對應檔案，請使用 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> 方法。  若要從現有檔案擷取存取規則或稽核規則，請使用 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> 方法。  
  
## 範例  
  
### 保存的記憶體對應檔案  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> 方法會從磁碟上的現有檔案建立記憶體對應檔案。  
  
 下列範例會對超大檔案的一部分建立記憶體對應檢視，並操作其中一部分。  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 下列範例會為另一個處理序開啟相同的記憶體對應檔案。  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### 非保存的記憶體對應檔案  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> 和 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> 方法會建立不對應至磁碟上現有檔案的記憶體對應檔案。  
  
 下列範例由三個獨立的處理序 \(主控台應用程式\) 所組成，這些處理序會將布林值寫入至記憶體對應檔案。  發生的動作序列如下：  
  
1.  `Process A` 建立記憶體對應檔案並在其中寫入值。  
  
2.  `Process B` 開啟記憶體對應檔案並在其中寫入值。  
  
3.  `Process C` 開啟記憶體對應檔案並在其中寫入值。  
  
4.  `Process A` 從記憶體對應檔案中讀取並顯示值。  
  
5.  在 `Process A` 完成處理記憶體對應檔案之後，檔案立即由記憶體回收作業回收。  
  
 若要執行此範例，請執行下列步驟：  
  
1.  編譯應用程式並開啟三個 \[命令提示字元\] 視窗。  
  
2.  在第一個命令提示字元視窗中執行 `Process A`。  
  
3.  在第二個命令提示字元視窗中執行 `Process B`。  
  
4.  回到 `Process A` 並按 ENTER 鍵。  
  
5.  在第三個命令提示字元視窗中執行 `Process C`。  
  
6.  回到 `Process A` 並按 ENTER 鍵。  
  
 `Process A` 的輸出如下：  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **處理序 A**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **處理序 B**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **處理序 C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## 請參閱  
 [檔案和資料流 I\/O](../../../docs/standard/io/index.md)