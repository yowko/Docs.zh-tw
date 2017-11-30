---
title: "如何：在隔離儲存區中建立檔案和目錄"
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
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b8a48473bf9ac91b89657d00d27031255491353
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="7cc45-102">如何：在隔離儲存區中建立檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="7cc45-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="7cc45-103">取得隔離存放區之後，您可以建立目錄和檔案來儲存資料。</span><span class="sxs-lookup"><span data-stu-id="7cc45-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="7cc45-104">存放區內，檔案和目錄名稱被指定相對於根目錄的虛擬檔案系統。</span><span class="sxs-lookup"><span data-stu-id="7cc45-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="7cc45-105">若要建立目錄，使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType>執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="7cc45-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="7cc45-106">如果您指定不存在目錄的子目錄，則會建立兩個目錄。</span><span class="sxs-lookup"><span data-stu-id="7cc45-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="7cc45-107">如果您指定的目錄已經存在，則方法會傳回而不需要建立一個目錄，並擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7cc45-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="7cc45-108">不過，如果您指定的目錄名稱包含無效的字元，<xref:System.IO.IsolatedStorage.IsolatedStorageException>擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7cc45-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="7cc45-109">若要建立檔案，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="7cc45-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="7cc45-110">在 Windows 作業系統、 隔離儲存區檔案和目錄名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="7cc45-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="7cc45-111">也就是說，如果您建立名為`ThisFile.txt`，然後再建立另一個名為的檔案`THISFILE.TXT`，會建立一個檔案。</span><span class="sxs-lookup"><span data-stu-id="7cc45-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="7cc45-112">檔案名稱會保留其原始大小寫用於顯示用途。</span><span class="sxs-lookup"><span data-stu-id="7cc45-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cc45-113">範例</span><span class="sxs-lookup"><span data-stu-id="7cc45-113">Example</span></span>  
 <span data-ttu-id="7cc45-114">下列程式碼範例說明如何在隔離存放區中建立檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="7cc45-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7cc45-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cc45-115">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [<span data-ttu-id="7cc45-116">隔離儲存區</span><span class="sxs-lookup"><span data-stu-id="7cc45-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
