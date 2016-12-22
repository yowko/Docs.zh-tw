---
title: "Classes Used in .NET Framework File I/O and the File System (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "file I/O classes"
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Classes Used in .NET Framework File I/O and the File System (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

下表會列出一般用於 .NET Framework 檔案 I\/O \(分類至檔案 I\/O 類別中\) 的類別、用於建立資料流的類別，以及用於讀取和寫入資料流的類別。  
  
 若要進入 [!INCLUDE[dnprdnlong](../../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] 文件尋找更完整的清單，請參閱 [類別庫概觀](../Topic/.NET%20Framework%20Class%20Library%20Overview.md)。  
  
## 檔案、磁碟機與目錄的基本 I\/O 類別  
 下表會列出並描述用於檔案 I\/O 的主要類別。  
  
|類別|描述|  
|--------|--------|  
|<xref:System.IO.Directory?displayProperty=fullName>|提供在所有目錄和子目錄中建立、移動和列舉的靜態方法。|  
|<xref:System.IO.DirectoryInfo?displayProperty=fullName>|提供在所有目錄和子目錄中建立、移動和列舉的執行個體方法 \(Instance Method\)。|  
|<xref:System.IO.DriveInfo?displayProperty=fullName>|提供在所有磁碟機中建立、移動和列舉的執行個體方法。|  
|<xref:System.IO.File?displayProperty=fullName>|提供建立、複製、刪除、移動和開啟檔案的靜態方法，並協助建立 `FileStream`。|  
|<xref:System.IO.FileAccess?displayProperty=fullName>|定義存取檔案的讀取、寫入或讀取\/寫入常數|  
|<xref:System.IO.FileAttributes?displayProperty=fullName>|提供檔案和目錄的屬性 \(Attribute\)，例如 `Archive`、`Hidden` 和 `ReadOnly`。|  
|<xref:System.IO.FileInfo?displayProperty=fullName>|提供建立、複製、刪除、移動和開啟檔案的靜態方法，並協助建立 `FileStream`。|  
|<xref:System.IO.FileMode?displayProperty=fullName>|控制開啟檔案的方法。  在 `FileStream` 和 `IsolatedStorageFileStream` 以及 <xref:System.IO.File> 和 <xref:System.IO.FileInfo> 之 `Open` 方法的許多建構函式 \(Constructor\) 中指定此參數。|  
|<xref:System.IO.FileShare?displayProperty=fullName>|定義常數，用以控制其他檔案資料流可以有相同檔案之存取權的類型。|  
|<xref:System.IO.Path?displayProperty=fullName>|提供用於處理目錄字串的方法和屬性。|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>|定義 <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>、<xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>、<xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> 和 <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> 存取權限，藉以控制檔案與資料夾的存取。|  
  
## 用於建立資料流的類別  
 下表會列出並描述用於建立資料流的主要類別。  
  
|類別|描述|  
|--------|--------|  
|<xref:System.IO.BufferedStream?displayProperty=fullName>|加入緩衝層，在另一個資料流上讀取與寫入作業。|  
|<xref:System.IO.FileStream?displayProperty=fullName>|透過其 <xref:System.IO.FileStream.Seek%2A> 方法支援對檔案的隨機存取。  <xref:System.IO.FileStream> 預設為同步開啟檔案，但也支援非同步作業。|  
|<xref:System.IO.MemoryStream?displayProperty=fullName>|建立資料流，而它的備份存放區是記憶體而不是檔案。|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=fullName>|針對網路存取提供資料的基礎資料流。|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=fullName>|定義連結資料流與密碼編譯轉換的資料流。|  
  
## 用於讀取和寫入資料流的類別  
 下表會顯示用於以資料流讀取和寫入檔案的特定類別。  
  
|**類別**|**描述**|  
|------------|------------|  
|<xref:System.IO.BinaryReader?displayProperty=fullName>|自 <xref:System.IO.FileStream> 讀取編碼字串與基本資料型別。|  
|<xref:System.IO.BinaryWriter?displayProperty=fullName>|將編碼字串與基本資料型別寫入 <xref:System.IO.FileStream>。|  
|<xref:System.IO.StreamReader?displayProperty=fullName>|使用 <xref:System.IO.StreamReader.CurrentEncoding%2A> 將字元轉換成位元組及轉換回字元，以便從 <xref:System.IO.FileStream> 讀取字元。  <xref:System.IO.StreamReader> 具有建構函式，會根據 <xref:System.IO.StreamReader.CurrentEncoding%2A> 特定前序編碼 \(例如位元組順序標記\) 的出現，嘗試斷定指定資料流的正確 <xref:System.IO.StreamReader.CurrentEncoding%2A>。|  
|<xref:System.IO.StreamWriter?displayProperty=fullName>|將字元寫入 `FileStream`，並使用 <xref:System.IO.StreamWriter.Encoding%2A> 將字元轉換為位元組。|  
|<xref:System.IO.StringReader?displayProperty=fullName>|讀取 `String` 中的字元。  輸出可以是採用任何編碼的資料流或是 `String`。|  
|<xref:System.IO.StringWriter?displayProperty=fullName>|將字元寫入 `String`。  輸出可以是採用任何編碼的資料流或是 `String`。|  
  
## 請參閱  
 [撰寫資料流](../Topic/Composing%20Streams.md)   
 [檔案和資料流 I\/O](../Topic/File%20and%20Stream%20I-O.md)   
 [非同步檔案 I\/O](../Topic/Asynchronous%20File%20I-O.md)   
 [.NET Framework 檔案 I\/O 和檔案系統基本概念 \(Visual Basic\)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)