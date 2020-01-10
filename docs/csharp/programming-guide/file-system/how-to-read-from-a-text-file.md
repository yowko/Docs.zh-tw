---
title: 如何從文字檔讀取-程式C#設計指南
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: d401a1d1bb2c6fccb203c440f367bd14c80e70e3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705011"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="bfb6d-102">如何從文字檔讀取（C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="bfb6d-102">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="bfb6d-103">這個範例會使用 <xref:System.IO.File?displayProperty=nameWithType> 類別中的靜態方法 <xref:System.IO.File.ReadAllText%2A> 和 <xref:System.IO.File.ReadAllLines%2A>，來讀取文字檔的內容。</span><span class="sxs-lookup"><span data-stu-id="bfb6d-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="bfb6d-104">如需使用 <xref:System.IO.StreamReader>的範例，請參閱[如何一次一行讀取文字檔](./how-to-read-a-text-file-one-line-at-a-time.md)。</span><span class="sxs-lookup"><span data-stu-id="bfb6d-104">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="bfb6d-105">本範例中使用的檔案是在[如何寫入文字檔](./how-to-write-to-a-text-file.md)主題中建立。</span><span class="sxs-lookup"><span data-stu-id="bfb6d-105">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="bfb6d-106">範例</span><span class="sxs-lookup"><span data-stu-id="bfb6d-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bfb6d-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bfb6d-107">Compiling the Code</span></span>  
 <span data-ttu-id="bfb6d-108">將程式碼複製並貼到 C# 主控台應用程式中。</span><span class="sxs-lookup"><span data-stu-id="bfb6d-108">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="bfb6d-109">如果您不是使用[如何寫入文字檔](./how-to-write-to-a-text-file.md)中的文字檔，請將引數取代為 `ReadAllText`，並在您的電腦上使用適當的路徑和檔案名 `ReadAllLines`。</span><span class="sxs-lookup"><span data-stu-id="bfb6d-109">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="bfb6d-110">最佳化程式設計</span><span class="sxs-lookup"><span data-stu-id="bfb6d-110">Robust Programming</span></span>  
 <span data-ttu-id="bfb6d-111">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="bfb6d-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="bfb6d-112">檔案不存在或不在指定的位置。</span><span class="sxs-lookup"><span data-stu-id="bfb6d-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="bfb6d-113">請檢查路徑和檔案名稱的拼字。</span><span class="sxs-lookup"><span data-stu-id="bfb6d-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bfb6d-114">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="bfb6d-114">.NET Framework Security</span></span>  
 <span data-ttu-id="bfb6d-115">請勿依賴檔案的名稱來判斷檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="bfb6d-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="bfb6d-116">例如，`myFile.cs` 檔案可能不是 C# 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="bfb6d-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb6d-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="bfb6d-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="bfb6d-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bfb6d-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bfb6d-119">檔案系統和登錄 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="bfb6d-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
