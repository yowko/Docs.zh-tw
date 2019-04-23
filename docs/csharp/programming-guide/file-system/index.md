---
title: 檔案系統和登錄 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: 64c852e6fcc034cb56651ffc2d22fa5323bbb54f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680060"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="6bf7f-102">檔案系統和登錄 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="6bf7f-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="6bf7f-103">下列主題示範如何使用 C# 和 .NET Framework 來針對檔案、資料夾及登錄執行各種基本作業。</span><span class="sxs-lookup"><span data-stu-id="6bf7f-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6bf7f-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="6bf7f-104">In This Section</span></span>  
  
|<span data-ttu-id="6bf7f-105">**標題**</span><span class="sxs-lookup"><span data-stu-id="6bf7f-105">**Title**</span></span>|<span data-ttu-id="6bf7f-106">**描述**</span><span class="sxs-lookup"><span data-stu-id="6bf7f-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="6bf7f-107">如何：逐一查看目錄樹狀結構</span><span class="sxs-lookup"><span data-stu-id="6bf7f-107">How to: Iterate Through a Directory Tree</span></span>](../../../csharp/programming-guide/file-system/how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="6bf7f-108">示範如何手動逐一查看樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="6bf7f-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="6bf7f-109">如何：取得有關檔案、資料夾和磁碟機的資訊</span><span class="sxs-lookup"><span data-stu-id="6bf7f-109">How to: Get Information About Files, Folders, and Drives</span></span>](../../../csharp/programming-guide/file-system/how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="6bf7f-110">示範如何擷取有關檔案、資料夾和磁碟機的資訊，例如建立時間和大小。</span><span class="sxs-lookup"><span data-stu-id="6bf7f-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="6bf7f-111">如何：建立檔案或資料夾</span><span class="sxs-lookup"><span data-stu-id="6bf7f-111">How to: Create a File or Folder</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-file-or-folder.md)|<span data-ttu-id="6bf7f-112">示範如何建立新檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="6bf7f-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="6bf7f-113">如何：複製、刪除和移動檔案和資料夾 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="6bf7f-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="6bf7f-114">示範如何複製、刪除和移動檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="6bf7f-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="6bf7f-115">如何：提供檔案作業的進度對話方塊</span><span class="sxs-lookup"><span data-stu-id="6bf7f-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="6bf7f-116">示範如何針對特定檔案作業顯示標準 Windows 進度對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6bf7f-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="6bf7f-117">如何：寫入文字檔</span><span class="sxs-lookup"><span data-stu-id="6bf7f-117">How to: Write to a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)|<span data-ttu-id="6bf7f-118">示範如何寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="6bf7f-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="6bf7f-119">如何：從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="6bf7f-119">How to: Read From a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-read-from-a-text-file.md)|<span data-ttu-id="6bf7f-120">示範如何從文字檔讀取。</span><span class="sxs-lookup"><span data-stu-id="6bf7f-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="6bf7f-121">如何：一次一行讀取文字檔</span><span class="sxs-lookup"><span data-stu-id="6bf7f-121">How to: Read a Text File One Line at a Time</span></span>](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="6bf7f-122">示範如何從檔案一次一行擷取文字。</span><span class="sxs-lookup"><span data-stu-id="6bf7f-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="6bf7f-123">如何：在登錄中建立機碼</span><span class="sxs-lookup"><span data-stu-id="6bf7f-123">How to: Create a Key In the Registry</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="6bf7f-124">示範如何將機碼寫入至系統登錄。</span><span class="sxs-lookup"><span data-stu-id="6bf7f-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="6bf7f-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="6bf7f-125">Related Sections</span></span>  
 [<span data-ttu-id="6bf7f-126">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="6bf7f-126">File and Stream I/O</span></span>](../../../standard/io/index.md)  
  
 [<span data-ttu-id="6bf7f-127">如何：複製、刪除和移動檔案和資料夾 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="6bf7f-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="6bf7f-128">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6bf7f-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
  
 [<span data-ttu-id="6bf7f-129">檔案、資料夾和磁碟機</span><span class="sxs-lookup"><span data-stu-id="6bf7f-129">Files, Folders and Drives</span></span>](../../../csharp/programming-guide/file-system/index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
