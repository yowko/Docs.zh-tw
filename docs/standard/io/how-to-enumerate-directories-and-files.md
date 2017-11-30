---
title: "如何：列舉目錄和檔案"
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
helpviewer_keywords: I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: caf9bdec017a5466269ff7fe97be4d0243035b4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="84023-102">如何：列舉目錄和檔案</span><span class="sxs-lookup"><span data-stu-id="84023-102">How to: Enumerate Directories and Files</span></span>
<span data-ttu-id="84023-103">您可以藉由傳回字串，其名稱的可列舉集合的方法來列舉目錄和檔案。</span><span class="sxs-lookup"><span data-stu-id="84023-103">You can enumerate directories and files by using methods that return an enumerable collection of strings of their names.</span></span> <span data-ttu-id="84023-104">您也可以使用傳回的可列舉集合的方法<xref:System.IO.DirectoryInfo>， <xref:System.IO.FileInfo>，或<xref:System.IO.FileSystemInfo>物件。</span><span class="sxs-lookup"><span data-stu-id="84023-104">You can also use methods that return an enumerable collection of <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span> <span data-ttu-id="84023-105">當您使用的目錄和檔案的大型集合，可列舉集合會提供更佳的效能比陣列。</span><span class="sxs-lookup"><span data-stu-id="84023-105">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span>  
  
 <span data-ttu-id="84023-106">您也可以使用這些方法從取得的可列舉集合，提供<xref:System.Collections.Generic.IEnumerable%601>參數集合的建構函式之類的類別<xref:System.Collections.Generic.List%601>類別。</span><span class="sxs-lookup"><span data-stu-id="84023-106">You can also use enumerable collections obtained from these methods to supply the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes such as the <xref:System.Collections.Generic.List%601> class.</span></span>  
  
 <span data-ttu-id="84023-107">如果您想要取得目錄或檔案的名稱，使用的列舉型別方法<xref:System.IO.Directory>類別。</span><span class="sxs-lookup"><span data-stu-id="84023-107">If you want to obtain only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="84023-108">如果您想要取得目錄或檔案的其他屬性，使用<xref:System.IO.DirectoryInfo>和<xref:System.IO.FileSystemInfo>類別。</span><span class="sxs-lookup"><span data-stu-id="84023-108">If you want to obtain other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
 <span data-ttu-id="84023-109">下表將提供指南，以傳回可列舉集合的方法。</span><span class="sxs-lookup"><span data-stu-id="84023-109">The following table provides a guide to the methods that return enumerable collections.</span></span>  
  
|<span data-ttu-id="84023-110">列舉</span><span class="sxs-lookup"><span data-stu-id="84023-110">To enumerate</span></span>|<span data-ttu-id="84023-111">要傳回的可列舉集合</span><span class="sxs-lookup"><span data-stu-id="84023-111">Enumerable collection to return</span></span>|<span data-ttu-id="84023-112">若要使用的方法</span><span class="sxs-lookup"><span data-stu-id="84023-112">Method to use</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="84023-113">目錄</span><span class="sxs-lookup"><span data-stu-id="84023-113">Directories</span></span>|<span data-ttu-id="84023-114">目錄名稱</span><span class="sxs-lookup"><span data-stu-id="84023-114">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="84023-115">目錄資訊 (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="84023-115">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84023-116">檔案</span><span class="sxs-lookup"><span data-stu-id="84023-116">Files</span></span>|<span data-ttu-id="84023-117">檔案名稱</span><span class="sxs-lookup"><span data-stu-id="84023-117">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="84023-118">檔案資訊 (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="84023-118">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84023-119">檔案系統資訊</span><span class="sxs-lookup"><span data-stu-id="84023-119">File system information</span></span>|<span data-ttu-id="84023-120">檔案系統項目</span><span class="sxs-lookup"><span data-stu-id="84023-120">File system entries</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="84023-121">檔案系統資訊 (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="84023-121">File system information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="84023-122">雖然您可以使用，以立即列舉父目錄的子目錄中的所有檔案<xref:System.IO.SearchOption.AllDirectories>搜尋所提供的選項<xref:System.IO.SearchOption>列舉型別、 未經授權的存取例外狀況 (<xref:System.UnauthorizedAccessException>) 可能會導致將列舉不完整。</span><span class="sxs-lookup"><span data-stu-id="84023-122">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> search option provided by the <xref:System.IO.SearchOption> enumeration, unauthorized access exceptions (<xref:System.UnauthorizedAccessException>) may cause the enumeration to be incomplete.</span></span> <span data-ttu-id="84023-123">如果可能會有這些例外狀況，您可以攔截，並繼續先列舉目錄和然後列舉檔案。</span><span class="sxs-lookup"><span data-stu-id="84023-123">If these exceptions are possible, you can catch them and continue by first enumerating directories and then enumerating files.</span></span>  
  
### <a name="to-enumerate-directory-names"></a><span data-ttu-id="84023-124">若要列舉的目錄名稱</span><span class="sxs-lookup"><span data-stu-id="84023-124">To enumerate directory names</span></span>  
  
-   <span data-ttu-id="84023-125">使用<xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType>方法，以取得指定之路徑中的最上層目錄名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="84023-125">Use the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to obtain a list of the top-level directory names in a specified path.</span></span>  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a><span data-ttu-id="84023-126">列舉目錄和子目錄中的檔案名稱</span><span class="sxs-lookup"><span data-stu-id="84023-126">To enumerate file names in a directory and subdirectories</span></span>  
  
-   <span data-ttu-id="84023-127">使用<xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType>方法來搜尋目錄，以及 （選擇性） 及其子目錄中，以及取得符合指定的搜尋模式的檔案名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="84023-127">Use the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to search a directory and (optionally) its subdirectories, and to obtain a list of file names that match a specified search pattern.</span></span>  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a><span data-ttu-id="84023-128">列舉 DirectoryInfo 物件的集合</span><span class="sxs-lookup"><span data-stu-id="84023-128">To enumerate a collection of DirectoryInfo objects</span></span>  
  
-   <span data-ttu-id="84023-129">使用<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>方法，以取得最上層目錄的集合。</span><span class="sxs-lookup"><span data-stu-id="84023-129">Use the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to obtain a collection of top-level directories.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a><span data-ttu-id="84023-130">若要列舉所有目錄中的 FileInfo 物件的集合</span><span class="sxs-lookup"><span data-stu-id="84023-130">To enumerate a collection of FileInfo objects in all directories</span></span>  
  
-   <span data-ttu-id="84023-131">使用<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>方法，以取得符合指定的搜尋模式的所有目錄中檔案的集合。</span><span class="sxs-lookup"><span data-stu-id="84023-131">Use the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to obtain a collection of files that match a specified search pattern in all directories.</span></span> <span data-ttu-id="84023-132">本範例先列舉攔截可能未經授權的存取例外狀況，最上層的目錄，然後列舉的檔案。</span><span class="sxs-lookup"><span data-stu-id="84023-132">This example first enumerates the top-level directories to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="84023-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84023-133">See Also</span></span>  
 [<span data-ttu-id="84023-134">檔案和資料流 I-O</span><span class="sxs-lookup"><span data-stu-id="84023-134">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
