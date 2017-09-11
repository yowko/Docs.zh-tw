---
title: "如何：複製、刪除和移動檔案和資料夾 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c7e9a170882c4e8dbb04dc014642a28ad4365e39
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="53201-102">如何：複製、刪除和移動檔案和資料夾 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="53201-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="53201-103">下列範例示範如何使用 <xref:System.IO?displayProperty=fullName> 命名空間的 <xref:System.IO.File?displayProperty=fullName>、<xref:System.IO.Directory?displayProperty=fullName>、<xref:System.IO.FileInfo?displayProperty=fullName> 和 <xref:System.IO.DirectoryInfo?displayProperty=fullName> 類別，以同步方式複製、移動及刪除檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="53201-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=fullName>, <xref:System.IO.Directory?displayProperty=fullName>, <xref:System.IO.FileInfo?displayProperty=fullName>, and <xref:System.IO.DirectoryInfo?displayProperty=fullName> classes from the <xref:System.IO?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="53201-104">這些範例不提供進度列或任何其他的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="53201-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="53201-105">如果您想要提供標準的進度對話方塊，請參閱[如何：提供檔案作業的進度對話方塊](how-to-provide-a-progress-dialog-box-for-file-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="53201-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="53201-106">操作多個檔案時，請使用 <xref:System.IO.FileSystemWatcher?displayProperty=fullName> 提供可讓您計算進度的事件。</span><span class="sxs-lookup"><span data-stu-id="53201-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=fullName> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="53201-107">另一種方法是使用平台叫用，在 Windows Shell 中呼叫與檔案有關的相關方法。</span><span class="sxs-lookup"><span data-stu-id="53201-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="53201-108">如需如何以非同步方式執行這些檔案作業的資訊，請參閱[非同步檔案 I/O](https://msdn.microsoft.com/library/kztecsys)。</span><span class="sxs-lookup"><span data-stu-id="53201-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](https://msdn.microsoft.com/library/kztecsys).</span></span>  
  
## <a name="example"></a><span data-ttu-id="53201-109">範例</span><span class="sxs-lookup"><span data-stu-id="53201-109">Example</span></span>  
 <span data-ttu-id="53201-110">下例示範如何複製檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="53201-110">The following example shows how to copy files and directories.</span></span>  
  
 <span data-ttu-id="53201-111">[!code-cs[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="53201-111">[!code-cs[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="53201-112">範例</span><span class="sxs-lookup"><span data-stu-id="53201-112">Example</span></span>  
 <span data-ttu-id="53201-113">下例示範如何移動檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="53201-113">The following example shows how to move files and directories.</span></span>  
  
 <span data-ttu-id="53201-114">[!code-cs[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="53201-114">[!code-cs[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="53201-115">範例</span><span class="sxs-lookup"><span data-stu-id="53201-115">Example</span></span>  
 <span data-ttu-id="53201-116">下例示範如何刪除檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="53201-116">The following example shows how to delete files and directories.</span></span>  
  
 <span data-ttu-id="53201-117">[!code-cs[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="53201-117">[!code-cs[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53201-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53201-118">See Also</span></span>  
 <span data-ttu-id="53201-119"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="53201-119"><xref:System.IO?displayProperty=fullName></span></span>   
<span data-ttu-id="53201-120"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="53201-120"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="53201-121"> [檔案系統和登錄 (C# 程式設計手冊)](index.md) </span><span class="sxs-lookup"><span data-stu-id="53201-121"> [File System and the Registry (C# Programming Guide)](index.md) </span></span>  
<span data-ttu-id="53201-122"> [如何：提供檔案作業的進度對話方塊](how-to-provide-a-progress-dialog-box-for-file-operations.md) </span><span class="sxs-lookup"><span data-stu-id="53201-122"> [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md) </span></span>  
<span data-ttu-id="53201-123"> [檔案和資料流 I/O](https://msdn.microsoft.com/library/k3352a4t) </span><span class="sxs-lookup"><span data-stu-id="53201-123"> [File and Stream I/O](https://msdn.microsoft.com/library/k3352a4t) </span></span>  
<span data-ttu-id="53201-124"> [一般 I/O 工作](https://msdn.microsoft.com/library/ms404278)</span><span class="sxs-lookup"><span data-stu-id="53201-124"> [Common I/O Tasks](https://msdn.microsoft.com/library/ms404278)</span></span>
