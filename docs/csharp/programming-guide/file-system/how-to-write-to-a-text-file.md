---
title: 作法：寫入文字檔 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: da1526afe48a0d4bda63274380dcf59ee30c480e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968796"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="631c2-102">HOW TO：寫入文字檔 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="631c2-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="631c2-103">在下列這些範例中，會示範幾個將文字寫入檔案的方法。</span><span class="sxs-lookup"><span data-stu-id="631c2-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="631c2-104">前兩個範例會在 <xref:System.IO.File?displayProperty=nameWithType> 類別上使用靜態便利方法，將任何 `IEnumerable<string>` 和字串的每個項目和字串寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="631c2-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="631c2-105">範例 3 中會示範寫入檔案時，如何在需要分別處理每一行時，將文字加入至檔案。</span><span class="sxs-lookup"><span data-stu-id="631c2-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="631c2-106">範例 1-3 會覆寫檔案中所有現有的內容，但是範例 4 將示範如何將文字附加至現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="631c2-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="631c2-107">這些範例全都會將字串常值寫入至檔案。</span><span class="sxs-lookup"><span data-stu-id="631c2-107">These examples all write string literals to files.</span></span> <span data-ttu-id="631c2-108">如果您想要格式化寫入檔案的文字，請使用 <xref:System.String.Format%2A> 方法或 C# [字串內插補點](../../../csharp/language-reference/tokens/interpolated.md)功能。</span><span class="sxs-lookup"><span data-stu-id="631c2-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../../csharp/language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="631c2-109">範例</span><span class="sxs-lookup"><span data-stu-id="631c2-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="631c2-110">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="631c2-110">Robust Programming</span></span>  
 <span data-ttu-id="631c2-111">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="631c2-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="631c2-112">該檔案存在而且是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="631c2-112">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="631c2-113">路徑名稱可能太長。</span><span class="sxs-lookup"><span data-stu-id="631c2-113">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="631c2-114">磁碟可能已滿。</span><span class="sxs-lookup"><span data-stu-id="631c2-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="631c2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="631c2-115">See also</span></span>

- [<span data-ttu-id="631c2-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="631c2-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="631c2-117">檔案系統和登錄 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="631c2-117">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
- [<span data-ttu-id="631c2-118">範例：如何將集合儲存至應用程式儲存空間</span><span class="sxs-lookup"><span data-stu-id="631c2-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
