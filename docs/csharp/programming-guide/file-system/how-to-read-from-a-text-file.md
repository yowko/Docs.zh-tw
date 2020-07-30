---
title: '如何從文字檔讀取-c # 程式設計手冊'
description: 瞭解如何使用 File 類別的靜態方法，從文字檔讀取。 查看程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 80ac6f8412f456b23d05ee87882dca8e16a132c3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301654"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="7e593-104">如何從文字檔讀取（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="7e593-104">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="7e593-105">這個範例會使用 <xref:System.IO.File?displayProperty=nameWithType> 類別中的靜態方法 <xref:System.IO.File.ReadAllText%2A> 和 <xref:System.IO.File.ReadAllLines%2A>，來讀取文字檔的內容。</span><span class="sxs-lookup"><span data-stu-id="7e593-105">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="7e593-106">如需使用的範例 <xref:System.IO.StreamReader> ，請參閱[如何一次一行讀取文字檔](./how-to-read-a-text-file-one-line-at-a-time.md)。</span><span class="sxs-lookup"><span data-stu-id="7e593-106">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="7e593-107">本範例中使用的檔案是在[如何寫入文字檔](./how-to-write-to-a-text-file.md)主題中建立。</span><span class="sxs-lookup"><span data-stu-id="7e593-107">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="7e593-108">範例</span><span class="sxs-lookup"><span data-stu-id="7e593-108">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7e593-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="7e593-109">Compiling the Code</span></span>  
 <span data-ttu-id="7e593-110">將程式碼複製並貼到 C# 主控台應用程式中。</span><span class="sxs-lookup"><span data-stu-id="7e593-110">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="7e593-111">如果您不是使用[如何寫入文字檔](./how-to-write-to-a-text-file.md)中的文字檔，請以 `ReadAllText` `ReadAllLines` 您電腦上的適當路徑和檔案名取代和的引數。</span><span class="sxs-lookup"><span data-stu-id="7e593-111">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="7e593-112">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="7e593-112">Robust Programming</span></span>  
 <span data-ttu-id="7e593-113">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="7e593-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="7e593-114">檔案不存在或不在指定的位置。</span><span class="sxs-lookup"><span data-stu-id="7e593-114">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="7e593-115">請檢查路徑和檔案名稱的拼字。</span><span class="sxs-lookup"><span data-stu-id="7e593-115">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="7e593-116">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="7e593-116">.NET Security</span></span>  
 <span data-ttu-id="7e593-117">請勿依賴檔案的名稱來判斷檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="7e593-117">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="7e593-118">例如，`myFile.cs` 檔案可能不是 C# 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="7e593-118">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e593-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e593-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="7e593-120">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7e593-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7e593-121">檔案系統和登錄 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="7e593-121">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
