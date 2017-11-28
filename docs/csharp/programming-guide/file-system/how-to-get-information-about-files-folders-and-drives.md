---
title: "如何：取得有關檔案、資料夾和磁碟機的資訊 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5652dda53a0192ce39be497b6e8ad3c97bef042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="da1aa-102">如何：取得有關檔案、資料夾和磁碟機的資訊 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="da1aa-102">How to: Get Information About Files, Folders, and Drives  (C# Programming Guide)</span></span>
<span data-ttu-id="da1aa-103">在 .NET Framework 中，您可以使用下列類別來存取檔案系統資訊：</span><span class="sxs-lookup"><span data-stu-id="da1aa-103">In the .NET Framework, you can access file system information by using the following classes:</span></span>  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="da1aa-104"><xref:System.IO.FileInfo> 和 <xref:System.IO.DirectoryInfo> 類別分別代表檔案和目錄，其所包含的屬性 (Property) 會公開 NTFS 檔案系統所支援的許多檔案屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="da1aa-104">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="da1aa-105">這些類別也包含用於開啟、關閉、移動及刪除檔案和資料夾的方法。</span><span class="sxs-lookup"><span data-stu-id="da1aa-105">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="da1aa-106">您可以將代表檔案、資料夾或磁碟機名稱的字串傳入建構函式，來建立這些類別的執行個體：</span><span class="sxs-lookup"><span data-stu-id="da1aa-106">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="da1aa-107">您也可以呼叫 <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>、<xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> 和 <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>，取得檔案、資料夾或磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="da1aa-107">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="da1aa-108"><xref:System.IO.Directory?displayProperty=nameWithType> 和 <xref:System.IO.File?displayProperty=nameWithType> 類別提供靜態方法，擷取目錄和檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="da1aa-108">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da1aa-109">範例</span><span class="sxs-lookup"><span data-stu-id="da1aa-109">Example</span></span>  
 <span data-ttu-id="da1aa-110">下列範例示範用來存取檔案和資料夾相關資訊的各種方法。</span><span class="sxs-lookup"><span data-stu-id="da1aa-110">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="da1aa-111">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="da1aa-111">Robust Programming</span></span>  
 <span data-ttu-id="da1aa-112">當您處理使用者指定的路徑字串時，您也應該處理下列情況所發生的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="da1aa-112">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
-   <span data-ttu-id="da1aa-113">檔案名稱的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="da1aa-113">The file name is malformed.</span></span> <span data-ttu-id="da1aa-114">例如，包含無效的字元，或只包含空白字元。</span><span class="sxs-lookup"><span data-stu-id="da1aa-114">For example, it contains invalid characters or only white space.</span></span>  
  
-   <span data-ttu-id="da1aa-115">檔案名稱為 null。</span><span class="sxs-lookup"><span data-stu-id="da1aa-115">The file name is null.</span></span>  
  
-   <span data-ttu-id="da1aa-116">檔案名稱超過系統定義的長度上限。</span><span class="sxs-lookup"><span data-stu-id="da1aa-116">The file name is longer than the system-defined maximum length.</span></span>  
  
-   <span data-ttu-id="da1aa-117">檔案名稱包含冒號 (:)。</span><span class="sxs-lookup"><span data-stu-id="da1aa-117">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="da1aa-118">如果應用程式沒有足夠的權限可讀取指定的檔案，則不論是否存在路徑，`Exists` 方法都會傳回 `false`；此方法不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="da1aa-118">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da1aa-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da1aa-119">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="da1aa-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="da1aa-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="da1aa-121">檔案系統和登錄 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="da1aa-121">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
