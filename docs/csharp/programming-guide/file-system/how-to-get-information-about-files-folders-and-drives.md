---
title: HOW TO：取得有關檔案、資料夾和磁碟機的資訊 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 7c122f0d342acb3708072be89e08c7465a654815
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660381"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>HOW TO：取得有關檔案、資料夾和磁碟機的資訊 (C# 程式設計手冊)
在 .NET Framework 中，您可以使用下列類別來存取檔案系統資訊：  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 <xref:System.IO.FileInfo> 和 <xref:System.IO.DirectoryInfo> 類別分別代表檔案和目錄，其所包含的屬性 (Property) 會公開 NTFS 檔案系統所支援的許多檔案屬性 (Attribute)。 這些類別也包含用於開啟、關閉、移動及刪除檔案和資料夾的方法。 您可以將代表檔案、資料夾或磁碟機名稱的字串傳入建構函式，來建立這些類別的執行個體：  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 您也可以呼叫 <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>、<xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> 和 <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>，取得檔案、資料夾或磁碟機名稱。  
  
 <xref:System.IO.Directory?displayProperty=nameWithType> 和 <xref:System.IO.File?displayProperty=nameWithType> 類別提供靜態方法，擷取目錄和檔案的相關資訊。  
  
## <a name="example"></a>範例  
 下列範例示範用來存取檔案和資料夾相關資訊的各種方法。  
  
 [!code-csharp[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 當您處理使用者指定的路徑字串時，您也應該處理下列情況所發生的例外狀況：  
  
-   檔案名稱的格式不正確。 例如，包含無效的字元，或只包含空白字元。  
  
-   檔案名稱為 null。  
  
-   檔案名稱超過系統定義的長度上限。  
  
-   檔案名稱包含冒號 (:)。  
  
 如果應用程式沒有足夠的權限可讀取指定的檔案，則不論是否存在路徑，`Exists` 方法都會傳回 `false`；此方法不會擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO?displayProperty=nameWithType>
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [檔案系統和登錄 (C# 程式設計指南)](../../../csharp/programming-guide/file-system/index.md)
