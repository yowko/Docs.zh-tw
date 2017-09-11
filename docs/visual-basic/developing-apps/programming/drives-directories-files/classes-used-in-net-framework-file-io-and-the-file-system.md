---
title: "用於 .NET Framework 檔案 I/O 和檔案系統的類別 (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a87d2e6f87b92b5f66706095d3f485c080008e0f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a><span data-ttu-id="0e515-102">用於 .NET Framework 檔案 I/O 和檔案系統的類別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e515-102">Classes Used in .NET Framework File I/O and the File System (Visual Basic)</span></span>
<span data-ttu-id="0e515-103">下列各表列出 .NET Framework 檔案 I/O 的常用類別、分類為檔案 I/O 類別的檔案、用於建立資料流的類別，以及用來讀取和寫入至資料流的類別。</span><span class="sxs-lookup"><span data-stu-id="0e515-103">The following tables list the classes commonly used for .NET Framework file I/O, categorized into file I/O classes, classes used for creating streams, and classes used to read and write to streams.</span></span>  
  
 <span data-ttu-id="0e515-104">若要輸入 [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] 文件，並尋找更完整的清單，請參閱[類別庫概觀](https://msdn.microsoft.com/library/hfa3fa08)。</span><span class="sxs-lookup"><span data-stu-id="0e515-104">To enter the [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] documentation and find a more comprehensive listing, see [Class Library Overview](https://msdn.microsoft.com/library/hfa3fa08).</span></span>  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a><span data-ttu-id="0e515-105">檔案、磁碟機和目錄的基本 I/O 類別</span><span class="sxs-lookup"><span data-stu-id="0e515-105">Basic I/O Classes for Files, Drives, and Directories</span></span>  
 <span data-ttu-id="0e515-106">下表列出並描述用於檔案 I/O 的主要類別。</span><span class="sxs-lookup"><span data-stu-id="0e515-106">The following table lists and describes the main classes used for file I/O.</span></span>  
  
|<span data-ttu-id="0e515-107">類別</span><span class="sxs-lookup"><span data-stu-id="0e515-107">Class</span></span>|<span data-ttu-id="0e515-108">說明</span><span class="sxs-lookup"><span data-stu-id="0e515-108">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=fullName>|<span data-ttu-id="0e515-109">提供建立、移動和列舉目錄和子目錄的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="0e515-109">Provides static methods for creating, moving, and enumerating through directories and subdirectories.</span></span>|  
|<xref:System.IO.DirectoryInfo?displayProperty=fullName>|<span data-ttu-id="0e515-110">提供建立、移動和列舉目錄和子目錄的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="0e515-110">Provides instance methods for creating, moving, and enumerating through directories and subdirectories.</span></span>|  
|<xref:System.IO.DriveInfo?displayProperty=fullName>|<span data-ttu-id="0e515-111">提供建立、移動和列舉磁碟機的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="0e515-111">Provides instance methods for creating, moving, and enumerating through drives.</span></span>|  
|<xref:System.IO.File?displayProperty=fullName>|<span data-ttu-id="0e515-112">提供建立、複製、刪除、移動和開啟檔案的靜態方法，並協助建立 `FileStream`。</span><span class="sxs-lookup"><span data-stu-id="0e515-112">Provides static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of a `FileStream`.</span></span>|  
|<xref:System.IO.FileAccess?displayProperty=fullName>|<span data-ttu-id="0e515-113">定義檔案讀取、寫入或讀取/寫入存取的常數。</span><span class="sxs-lookup"><span data-stu-id="0e515-113">Defines constants for read, write, or read/write access to a file.</span></span>|  
|<xref:System.IO.FileAttributes?displayProperty=fullName>|<span data-ttu-id="0e515-114">提供檔案和目錄的屬性，例如 `Archive`、`Hidden` 和 `ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="0e515-114">Provides attributes for files and directories such as `Archive`, `Hidden`, and `ReadOnly`.</span></span>|  
|<xref:System.IO.FileInfo?displayProperty=fullName>|<span data-ttu-id="0e515-115">提供建立、複製、刪除、移動和開啟檔案的靜態方法，並協助建立 `FileStream`。</span><span class="sxs-lookup"><span data-stu-id="0e515-115">Provides static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of a `FileStream`.</span></span>|  
|<xref:System.IO.FileMode?displayProperty=fullName>|<span data-ttu-id="0e515-116">控制檔案的開啟方式。</span><span class="sxs-lookup"><span data-stu-id="0e515-116">Controls how a file is opened.</span></span> <span data-ttu-id="0e515-117">這個參數於針對 `FileStream` 和 `IsolatedStorageFileStream`，以及針對 <xref:System.IO.File> 和 <xref:System.IO.FileInfo> 之 `Open` 方法的許多建構函式中指定。</span><span class="sxs-lookup"><span data-stu-id="0e515-117">This parameter is specified in many of the constructors for `FileStream` and `IsolatedStorageFileStream`, and for the `Open` methods of <xref:System.IO.File> and <xref:System.IO.FileInfo>.</span></span>|  
|<xref:System.IO.FileShare?displayProperty=fullName>|<span data-ttu-id="0e515-118">定義常數，用來控制其他檔案資料流對相同檔案可以擁有的存取類型。</span><span class="sxs-lookup"><span data-stu-id="0e515-118">Defines constants for controlling the type of access other file streams can have to the same file.</span></span>|  
|<xref:System.IO.Path?displayProperty=fullName>|<span data-ttu-id="0e515-119">提供處理目錄字串的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="0e515-119">Provides methods and properties for processing directory strings.</span></span>|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>|<span data-ttu-id="0e515-120">透過定義 <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>、<xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>、<xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A>，以及 <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> 權限，來控制檔案和資料夾的存取。</span><span class="sxs-lookup"><span data-stu-id="0e515-120">Controls the access of files and folders by defining <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> and <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> permissions.</span></span>|  
  
## <a name="classes-used-to-create-streams"></a><span data-ttu-id="0e515-121">用來建立資料流的類別</span><span class="sxs-lookup"><span data-stu-id="0e515-121">Classes Used to Create Streams</span></span>  
 <span data-ttu-id="0e515-122">下表列出並描述用來建立資料流的主要類別。</span><span class="sxs-lookup"><span data-stu-id="0e515-122">The following table lists and describes the main classes used to create streams.</span></span>  
  
|<span data-ttu-id="0e515-123">類別</span><span class="sxs-lookup"><span data-stu-id="0e515-123">Class</span></span>|<span data-ttu-id="0e515-124">說明</span><span class="sxs-lookup"><span data-stu-id="0e515-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=fullName>|<span data-ttu-id="0e515-125">新增另一個資料流上讀取和寫入作業的緩衝層。</span><span class="sxs-lookup"><span data-stu-id="0e515-125">Adds a buffering layer to read and write operations on another stream.</span></span>|  
|<xref:System.IO.FileStream?displayProperty=fullName>|<span data-ttu-id="0e515-126">透過類別的 <xref:System.IO.FileStream.Seek%2A> 方法，支援對檔案的隨機存取。</span><span class="sxs-lookup"><span data-stu-id="0e515-126">Supports random access to files through its <xref:System.IO.FileStream.Seek%2A> method.</span></span> <span data-ttu-id="0e515-127"><xref:System.IO.FileStream> 預設會以同步的方式開啟檔案，但也支援非同步作業。</span><span class="sxs-lookup"><span data-stu-id="0e515-127"><xref:System.IO.FileStream> opens files synchronously by default but also supports asynchronous operation.</span></span>|  
|<xref:System.IO.MemoryStream?displayProperty=fullName>|<span data-ttu-id="0e515-128">建立支援的存放區為記憶體而非檔案的資料流。</span><span class="sxs-lookup"><span data-stu-id="0e515-128">Creates a stream whose backing store is memory, rather than a file.</span></span>|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=fullName>|<span data-ttu-id="0e515-129">提供基礎資料流以進行網路存取。</span><span class="sxs-lookup"><span data-stu-id="0e515-129">Provides the underlying stream of data for network access.</span></span>|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=fullName>|<span data-ttu-id="0e515-130">定義連結資料流與密碼編譯轉換的資料流。</span><span class="sxs-lookup"><span data-stu-id="0e515-130">Defines a stream that links data streams to cryptographic transformations.</span></span>|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a><span data-ttu-id="0e515-131">用來讀取和寫入至資料流的類別</span><span class="sxs-lookup"><span data-stu-id="0e515-131">Classes Used to Read from and Write to Streams</span></span>  
 <span data-ttu-id="0e515-132">下表顯示用於讀取和寫入至具有資料流之檔案的特定類別。</span><span class="sxs-lookup"><span data-stu-id="0e515-132">The following table shows the specific classes used for reading from and writing to files with streams.</span></span>  
  
|<span data-ttu-id="0e515-133">**類別**</span><span class="sxs-lookup"><span data-stu-id="0e515-133">**Class**</span></span>|<span data-ttu-id="0e515-134">**說明**</span><span class="sxs-lookup"><span data-stu-id="0e515-134">**Description**</span></span>|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=fullName>|<span data-ttu-id="0e515-135">從 <xref:System.IO.FileStream> 讀取編碼字串和基本資料類型。</span><span class="sxs-lookup"><span data-stu-id="0e515-135">Reads encoded strings and primitive data types from a <xref:System.IO.FileStream>.</span></span>|  
|<xref:System.IO.BinaryWriter?displayProperty=fullName>|<span data-ttu-id="0e515-136">將編碼字串和基本資料類型寫入 <xref:System.IO.FileStream>。</span><span class="sxs-lookup"><span data-stu-id="0e515-136">Writes encoded strings and primitive data types to a <xref:System.IO.FileStream>.</span></span>|  
|<xref:System.IO.StreamReader?displayProperty=fullName>|<span data-ttu-id="0e515-137">從 <xref:System.IO.FileStream> 讀取字元，使用 <xref:System.IO.StreamReader.CurrentEncoding%2A> 來在字元與位元組之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="0e515-137">Reads characters from a <xref:System.IO.FileStream>, using <xref:System.IO.StreamReader.CurrentEncoding%2A> to convert characters to and from bytes.</span></span> <span data-ttu-id="0e515-138"><xref:System.IO.StreamReader> 具有會根據 <xref:System.IO.StreamReader.CurrentEncoding%2A> 特定的前序 (例如位元組順序標記) 是否存在，來嘗試針對特定資料流確認正確 <xref:System.IO.StreamReader.CurrentEncoding%2A> 的建構函式。</span><span class="sxs-lookup"><span data-stu-id="0e515-138"><xref:System.IO.StreamReader> has a constructor that attempts to ascertain the correct <xref:System.IO.StreamReader.CurrentEncoding%2A> for a given stream, based on the presence of a <xref:System.IO.StreamReader.CurrentEncoding%2A>-specific preamble, such as a byte order mark.</span></span>|  
|<xref:System.IO.StreamWriter?displayProperty=fullName>|<span data-ttu-id="0e515-139">將字元寫入 `FileStream`，使用 <xref:System.IO.StreamWriter.Encoding%2A> 將字元轉換成位元組。</span><span class="sxs-lookup"><span data-stu-id="0e515-139">Writes characters to a `FileStream`, using <xref:System.IO.StreamWriter.Encoding%2A> to convert characters to bytes.</span></span>|  
|<xref:System.IO.StringReader?displayProperty=fullName>|<span data-ttu-id="0e515-140">從 `String` 讀取字元。</span><span class="sxs-lookup"><span data-stu-id="0e515-140">Reads characters from a `String`.</span></span> <span data-ttu-id="0e515-141">輸出可以是任何編碼的資料流或 `String`。</span><span class="sxs-lookup"><span data-stu-id="0e515-141">Output can be either a stream in any encoding or a `String`.</span></span>|  
|<xref:System.IO.StringWriter?displayProperty=fullName>|<span data-ttu-id="0e515-142">將字元寫入至 `String`。</span><span class="sxs-lookup"><span data-stu-id="0e515-142">Writes characters to a `String`.</span></span> <span data-ttu-id="0e515-143">輸出可以是任何編碼的資料流或 `String`。</span><span class="sxs-lookup"><span data-stu-id="0e515-143">Output can be either a stream in any encoding or a `String`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e515-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e515-144">See Also</span></span>  
 <span data-ttu-id="0e515-145">[撰寫資料流](https://msdn.microsoft.com/library/e4y2dch9) </span><span class="sxs-lookup"><span data-stu-id="0e515-145">[Composing Streams](https://msdn.microsoft.com/library/e4y2dch9) </span></span>  
 <span data-ttu-id="0e515-146">[檔案和資料流 I/O](https://msdn.microsoft.com/library/k3352a4t) </span><span class="sxs-lookup"><span data-stu-id="0e515-146">[File and Stream I/O](https://msdn.microsoft.com/library/k3352a4t) </span></span>  
 <span data-ttu-id="0e515-147">[非同步檔案 I/O](https://msdn.microsoft.com/library/kztecsys) </span><span class="sxs-lookup"><span data-stu-id="0e515-147">[Asynchronous File I/O](https://msdn.microsoft.com/library/kztecsys) </span></span>  
 [<span data-ttu-id="0e515-148">.NET Framework 檔案 I/O 和檔案系統基本概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e515-148">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)

