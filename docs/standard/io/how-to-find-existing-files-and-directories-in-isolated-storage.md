---
title: 如何：尋找隔離儲存區中的現有檔案和目錄
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET Framework], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET Framework], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 866be7970c43051dd7e2bf8d45ae779aca130a45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574874"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="147ef-102">如何：尋找隔離儲存區中的現有檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="147ef-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="147ef-103">若要搜尋隔離儲存區中的目錄，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="147ef-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="147ef-104">此方法會採用表示搜尋模式的字串。</span><span class="sxs-lookup"><span data-stu-id="147ef-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="147ef-105">您可以在搜尋模式中使用單一字元 (?) 和多重字元 (\*) 萬用字元，但萬用字元必須出現在名稱的最後一個部分。</span><span class="sxs-lookup"><span data-stu-id="147ef-105">You can use both single-character (?) and multi-character (\*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="147ef-106">例如，`directory1/*ect*` 是有效的搜尋字串，但 `*ect*/directory2` 不是。</span><span class="sxs-lookup"><span data-stu-id="147ef-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="147ef-107">若要搜尋檔案，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="147ef-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="147ef-108">在搜尋字串中，適用於 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> 的萬用字元限制也適用於 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>。</span><span class="sxs-lookup"><span data-stu-id="147ef-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="147ef-109">這些都不是遞迴方法。<xref:System.IO.IsolatedStorage.IsolatedStorageFile> 類別不會提供任何方法來列出存放區中的所有目錄或檔案。</span><span class="sxs-lookup"><span data-stu-id="147ef-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="147ef-110">不過，遞迴方法會顯示在下列程式碼範例中。</span><span class="sxs-lookup"><span data-stu-id="147ef-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="147ef-111">範例</span><span class="sxs-lookup"><span data-stu-id="147ef-111">Example</span></span>  
 <span data-ttu-id="147ef-112">下列程式碼範例說明如何在隔離存放區中建立檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="147ef-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="147ef-113">首先，系統會擷取針對使用者、網域和組件所隔離的存放區，並放置在 `isoStore` 變數中。</span><span class="sxs-lookup"><span data-stu-id="147ef-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="147ef-114"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> 方法用來設定幾個不同的目錄，而 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> 建構函式會在這些目錄中建立一些檔案。</span><span class="sxs-lookup"><span data-stu-id="147ef-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="147ef-115">接著，此程式碼會在 `GetAllDirectories` 方法的結果中執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="147ef-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="147ef-116">此方法會使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> 尋找目前目錄中的所有目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="147ef-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="147ef-117">這些名稱會儲存在陣列中，然後 `GetAllDirectories` 會呼叫其本身，進而傳入所找到的每個目錄。</span><span class="sxs-lookup"><span data-stu-id="147ef-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="147ef-118">因此，陣列中會傳回所有目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="147ef-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="147ef-119">接下來，此程式碼會呼叫 `GetAllFiles` 方法。</span><span class="sxs-lookup"><span data-stu-id="147ef-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="147ef-120">此方法會呼叫 `GetAllDirectories` 來找出所有目錄的名稱，然後使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> 方法檢查每個目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="147ef-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="147ef-121">陣列中會傳回結果以供顯示。</span><span class="sxs-lookup"><span data-stu-id="147ef-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="147ef-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="147ef-122">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="147ef-123">隔離儲存區</span><span class="sxs-lookup"><span data-stu-id="147ef-123">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
