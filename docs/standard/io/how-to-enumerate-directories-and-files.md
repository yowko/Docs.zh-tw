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
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5d0f22853210144881e49c4192ea38a5c3e57cda
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="97d48-102">如何：列舉目錄和檔案</span><span class="sxs-lookup"><span data-stu-id="97d48-102">How to: Enumerate Directories and Files</span></span>
<span data-ttu-id="97d48-103">您可以使用能夠傳回可列舉其名稱字串集合的方法來列舉目錄和檔案。</span><span class="sxs-lookup"><span data-stu-id="97d48-103">You can enumerate directories and files by using methods that return an enumerable collection of strings of their names.</span></span> <span data-ttu-id="97d48-104">您也可以使用傳回可列舉 <xref:System.IO.DirectoryInfo>、<xref:System.IO.FileInfo> 或 <xref:System.IO.FileSystemInfo> 物件集合的方法。</span><span class="sxs-lookup"><span data-stu-id="97d48-104">You can also use methods that return an enumerable collection of <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span> <span data-ttu-id="97d48-105">當您使用目錄和檔案的大型集合時，相較於陣列，可列舉的集合會提供更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="97d48-105">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span>  
  
 <span data-ttu-id="97d48-106">您也可以使用取自這些方法的可列舉集合，為集合類別的建構函式提供 <xref:System.Collections.Generic.IEnumerable%601> 參數，例如 <xref:System.Collections.Generic.List%601> 類別。</span><span class="sxs-lookup"><span data-stu-id="97d48-106">You can also use enumerable collections obtained from these methods to supply the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes such as the <xref:System.Collections.Generic.List%601> class.</span></span>  
  
 <span data-ttu-id="97d48-107">如果您想要只取得目錄或檔案的名稱，請使用 <xref:System.IO.Directory> 類別的列舉方法。</span><span class="sxs-lookup"><span data-stu-id="97d48-107">If you want to obtain only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="97d48-108">如果您想要取得目錄或檔案的其他屬性，請使用 <xref:System.IO.DirectoryInfo> 和 <xref:System.IO.FileSystemInfo> 類別。</span><span class="sxs-lookup"><span data-stu-id="97d48-108">If you want to obtain other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
 <span data-ttu-id="97d48-109">下表將針對傳回可列舉集合的方法，提供指南。</span><span class="sxs-lookup"><span data-stu-id="97d48-109">The following table provides a guide to the methods that return enumerable collections.</span></span>  
  
|<span data-ttu-id="97d48-110">列舉</span><span class="sxs-lookup"><span data-stu-id="97d48-110">To enumerate</span></span>|<span data-ttu-id="97d48-111">要傳回的可列舉集合</span><span class="sxs-lookup"><span data-stu-id="97d48-111">Enumerable collection to return</span></span>|<span data-ttu-id="97d48-112">要使用的方法</span><span class="sxs-lookup"><span data-stu-id="97d48-112">Method to use</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="97d48-113">目錄</span><span class="sxs-lookup"><span data-stu-id="97d48-113">Directories</span></span>|<span data-ttu-id="97d48-114">目錄名稱</span><span class="sxs-lookup"><span data-stu-id="97d48-114">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="97d48-115">虛擬資訊 (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="97d48-115">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="97d48-116">檔案</span><span class="sxs-lookup"><span data-stu-id="97d48-116">Files</span></span>|<span data-ttu-id="97d48-117">檔案名稱</span><span class="sxs-lookup"><span data-stu-id="97d48-117">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="97d48-118">檔案資訊 (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="97d48-118">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="97d48-119">檔案系統資訊</span><span class="sxs-lookup"><span data-stu-id="97d48-119">File system information</span></span>|<span data-ttu-id="97d48-120">檔案系統項目</span><span class="sxs-lookup"><span data-stu-id="97d48-120">File system entries</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="97d48-121">檔案系統資訊 (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="97d48-121">File system information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="97d48-122">雖然您可以使用 <xref:System.IO.SearchOption> 列舉提供的 <xref:System.IO.SearchOption.AllDirectories> 搜尋選項立即列舉父目錄之子目錄中的所有檔案，但是未經授權的存取例外狀況 (<xref:System.UnauthorizedAccessException>) 可能會導致列舉不完整。</span><span class="sxs-lookup"><span data-stu-id="97d48-122">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> search option provided by the <xref:System.IO.SearchOption> enumeration, unauthorized access exceptions (<xref:System.UnauthorizedAccessException>) may cause the enumeration to be incomplete.</span></span> <span data-ttu-id="97d48-123">如果可能有這些例外狀況，您可以先列舉目錄再列舉檔案來攔截這些例外狀況，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="97d48-123">If these exceptions are possible, you can catch them and continue by first enumerating directories and then enumerating files.</span></span>  
  
### <a name="to-enumerate-directory-names"></a><span data-ttu-id="97d48-124">若要列舉目錄名稱</span><span class="sxs-lookup"><span data-stu-id="97d48-124">To enumerate directory names</span></span>  
  
-   <span data-ttu-id="97d48-125">使用 <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> 方法，在指定的路徑中取得最上層目錄名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="97d48-125">Use the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to obtain a list of the top-level directory names in a specified path.</span></span>  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a><span data-ttu-id="97d48-126">若要列舉目錄和子目錄中的檔案名稱</span><span class="sxs-lookup"><span data-stu-id="97d48-126">To enumerate file names in a directory and subdirectories</span></span>  
  
-   <span data-ttu-id="97d48-127">使用 <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> 方法搜尋目錄及 (選擇性) 其子目錄，並取得符合指定之搜尋模式的檔案名稱清單。</span><span class="sxs-lookup"><span data-stu-id="97d48-127">Use the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to search a directory and (optionally) its subdirectories, and to obtain a list of file names that match a specified search pattern.</span></span>  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a><span data-ttu-id="97d48-128">若要列舉 DirectoryInfo 物件的集合</span><span class="sxs-lookup"><span data-stu-id="97d48-128">To enumerate a collection of DirectoryInfo objects</span></span>  
  
-   <span data-ttu-id="97d48-129">使用 <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> 方法取得最上層目錄的集合。</span><span class="sxs-lookup"><span data-stu-id="97d48-129">Use the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to obtain a collection of top-level directories.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a><span data-ttu-id="97d48-130">若要列舉所有目錄中 FileInfo 物件的集合</span><span class="sxs-lookup"><span data-stu-id="97d48-130">To enumerate a collection of FileInfo objects in all directories</span></span>  
  
-   <span data-ttu-id="97d48-131">使用 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> 方法，取得符合所有目錄中指定之搜尋模式的檔案集合。</span><span class="sxs-lookup"><span data-stu-id="97d48-131">Use the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to obtain a collection of files that match a specified search pattern in all directories.</span></span> <span data-ttu-id="97d48-132">此範例會先列舉最上層目錄來攔截可能未經授權的存取例外狀況，然後再列舉檔案。</span><span class="sxs-lookup"><span data-stu-id="97d48-132">This example first enumerates the top-level directories to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="97d48-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="97d48-133">See Also</span></span>  
 [<span data-ttu-id="97d48-134">檔案和資料流 I-O</span><span class="sxs-lookup"><span data-stu-id="97d48-134">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
