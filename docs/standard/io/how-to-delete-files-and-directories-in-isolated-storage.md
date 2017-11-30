---
title: "如何：刪除隔離儲存區中的檔案和目錄"
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
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 971f27cd25cbe4be3ca3fad6283ab32d4f6db0ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="a92ce-102">如何：刪除隔離儲存區中的檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="a92ce-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="a92ce-103">您可以刪除目錄和檔案中的隔離儲存區檔案。</span><span class="sxs-lookup"><span data-stu-id="a92ce-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="a92ce-104">存放區內，檔案和目錄名稱會是作業系統相依性，且指定相對於根目錄的虛擬檔案系統。</span><span class="sxs-lookup"><span data-stu-id="a92ce-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="a92ce-105">它們是不區分大小寫，在 Windows 作業系統上。</span><span class="sxs-lookup"><span data-stu-id="a92ce-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="a92ce-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>類別提供兩個方法來刪除目錄和檔案：<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>和<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>。</span><span class="sxs-lookup"><span data-stu-id="a92ce-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="a92ce-107"><xref:System.IO.IsolatedStorage.IsolatedStorageException>如果您嘗試刪除檔案或目錄不存在，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a92ce-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="a92ce-108">如果您在名稱中包含萬用字元<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>會擲回<xref:System.IO.IsolatedStorage.IsolatedStorageException>例外狀況，以及<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>會擲回<xref:System.ArgumentException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a92ce-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="a92ce-109"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>方法失敗時，如果目錄中包含任何檔案或子目錄。</span><span class="sxs-lookup"><span data-stu-id="a92ce-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="a92ce-110">您可以使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>和<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>方法來擷取現有的檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="a92ce-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="a92ce-111">如需搜尋虛擬檔案系統中的存放區的詳細資訊，請參閱[How to： 隔離儲存區中尋找現有的檔案和目錄](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)。</span><span class="sxs-lookup"><span data-stu-id="a92ce-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a92ce-112">範例</span><span class="sxs-lookup"><span data-stu-id="a92ce-112">Example</span></span>  
 <span data-ttu-id="a92ce-113">下列程式碼範例會建立，，然後刪除 數個目錄和檔案。</span><span class="sxs-lookup"><span data-stu-id="a92ce-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a92ce-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a92ce-114">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
 [<span data-ttu-id="a92ce-115">隔離儲存區</span><span class="sxs-lookup"><span data-stu-id="a92ce-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
