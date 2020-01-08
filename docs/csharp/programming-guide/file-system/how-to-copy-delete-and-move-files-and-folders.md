---
title: 如何複製、刪除和移動檔案和資料夾-程式C#設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 234e534ef081d3ab527d307b9d3f1756783ad5ac
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635557"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="5128a-102">如何複製、刪除和移動檔案和資料夾（C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="5128a-102">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>
<span data-ttu-id="5128a-103">下列範例會示範如何使用 <xref:System.IO?displayProperty=nameWithType> 命名空間的 <xref:System.IO.File?displayProperty=nameWithType>、<xref:System.IO.Directory?displayProperty=nameWithType>、<xref:System.IO.FileInfo?displayProperty=nameWithType> 和 <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> 類別，以同步方式複製、移動和刪除檔案與資料夾。</span><span class="sxs-lookup"><span data-stu-id="5128a-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="5128a-104">這些範例不提供進度列或任何其他的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="5128a-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="5128a-105">如果您想要提供標準的進度對話方塊，請參閱[如何提供檔案作業的進度對話方塊](how-to-provide-a-progress-dialog-box-for-file-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="5128a-105">If you want to provide a standard progress dialog box, see [How to provide a progress dialog box for file operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="5128a-106">操作多個檔案時，使用 <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> 提供可讓您計算進度的事件。</span><span class="sxs-lookup"><span data-stu-id="5128a-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="5128a-107">另一種方法是使用平台叫用，在 Windows Shell 中呼叫與檔案有關的相關方法。</span><span class="sxs-lookup"><span data-stu-id="5128a-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="5128a-108">如需如何以非同步方式執行這些檔案作業的資訊，請參閱[非同步檔案 I/O](../../../standard/io/asynchronous-file-i-o.md)。</span><span class="sxs-lookup"><span data-stu-id="5128a-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5128a-109">範例</span><span class="sxs-lookup"><span data-stu-id="5128a-109">Example</span></span>  
 <span data-ttu-id="5128a-110">下例示範如何複製檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="5128a-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="5128a-111">範例</span><span class="sxs-lookup"><span data-stu-id="5128a-111">Example</span></span>  
 <span data-ttu-id="5128a-112">下例示範如何移動檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="5128a-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="5128a-113">範例</span><span class="sxs-lookup"><span data-stu-id="5128a-113">Example</span></span>  
 <span data-ttu-id="5128a-114">下例示範如何刪除檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="5128a-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="5128a-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="5128a-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="5128a-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5128a-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5128a-117">檔案系統和登錄 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5128a-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="5128a-118">如何提供檔案作業的進度對話方塊</span><span class="sxs-lookup"><span data-stu-id="5128a-118">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="5128a-119">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="5128a-119">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="5128a-120">一般 I/O 工作</span><span class="sxs-lookup"><span data-stu-id="5128a-120">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
