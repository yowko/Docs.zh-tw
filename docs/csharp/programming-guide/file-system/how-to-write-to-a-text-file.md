---
title: '如何寫入文字檔-c # 程式設計手冊'
description: '瞭解如何使用 c # 撰寫文字檔。 查看數個程式碼範例，並查看其他可用的資源。'
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: 48739852cd1730d71c3b20ae6a9394b57785faa6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170398"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="cba07-104">如何寫入文字檔 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="cba07-104">How to write to a text file (C# Programming Guide)</span></span>

<span data-ttu-id="cba07-105">在下列這些範例中，會示範幾個將文字寫入檔案的方法。</span><span class="sxs-lookup"><span data-stu-id="cba07-105">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="cba07-106">前兩個範例會在 <xref:System.IO.File?displayProperty=nameWithType> 類別上使用靜態便利方法，將任何 `IEnumerable<string>` 和字串的每個項目和字串寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="cba07-106">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="cba07-107">範例 3 中會示範寫入檔案時，如何在需要分別處理每一行時，將文字加入至檔案。</span><span class="sxs-lookup"><span data-stu-id="cba07-107">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="cba07-108">範例 1-3 會覆寫檔案中所有現有的內容，但是範例 4 將示範如何將文字附加至現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="cba07-108">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="cba07-109">這些範例全都會將字串常值寫入至檔案。</span><span class="sxs-lookup"><span data-stu-id="cba07-109">These examples all write string literals to files.</span></span> <span data-ttu-id="cba07-110">如果您想要格式化寫入檔案的文字，請使用 <xref:System.String.Format%2A> 方法或 C# [字串內插補點](../../language-reference/tokens/interpolated.md)功能。</span><span class="sxs-lookup"><span data-stu-id="cba07-110">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cba07-111">範例</span><span class="sxs-lookup"><span data-stu-id="cba07-111">Example</span></span>  

 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cba07-112">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="cba07-112">Robust Programming</span></span>  

 <span data-ttu-id="cba07-113">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="cba07-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="cba07-114">該檔案存在而且是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="cba07-114">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="cba07-115">路徑名稱可能太長。</span><span class="sxs-lookup"><span data-stu-id="cba07-115">The path name may be too long.</span></span>  
  
- <span data-ttu-id="cba07-116">磁碟可能已滿。</span><span class="sxs-lookup"><span data-stu-id="cba07-116">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba07-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cba07-117">See also</span></span>

- [<span data-ttu-id="cba07-118">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cba07-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cba07-119">檔案系統和登錄 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="cba07-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="cba07-120">範例：如何將集合儲存至應用程式儲存空間</span><span class="sxs-lookup"><span data-stu-id="cba07-120">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
