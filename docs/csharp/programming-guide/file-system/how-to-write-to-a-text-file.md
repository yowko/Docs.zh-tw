---
title: "如何：寫入文字檔 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
dev_langs:
- CSharp
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: 23
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
ms.openlocfilehash: c56095582561e4df19b164bc9a46b69a14da7c9d
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="c3cbd-102">如何：寫入文字檔 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c3cbd-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="c3cbd-103">在下列這些範例中，會示範幾個將文字寫入檔案的方法。</span><span class="sxs-lookup"><span data-stu-id="c3cbd-103">These examples show various ways to write text to a file.</span></span>  <span data-ttu-id="c3cbd-104">前兩個範例會在 <xref:System.IO.File?displayProperty=fullName> 類別上使用靜態便利方法，將任何 IEnumerable\<string> 的每個項目和字串寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="c3cbd-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=fullName> class to write each element of any IEnumerable\<string> and a string to a text file.</span></span>  <span data-ttu-id="c3cbd-105">範例 3 中會示範寫入檔案時，如何在需要分別處理每一行時，將文字加入至檔案。</span><span class="sxs-lookup"><span data-stu-id="c3cbd-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span>  <span data-ttu-id="c3cbd-106">範例 1-3 會覆寫檔案中所有現有的內容，但是範例 4 將示範如何將文字附加至現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="c3cbd-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="c3cbd-107">這些範例全都會將字串常值寫入至檔案，不過您可能比較想要使用 <xref:System.String.Format%2A> 方法，該方法提供許多控制項讓您撰寫不同類型的值，在欄位中靠右或靠左對齊、使用或不使用邊框間距等等。</span><span class="sxs-lookup"><span data-stu-id="c3cbd-107">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="c3cbd-108">您也可以使用 C# [字串插值](../../../csharp/language-reference/keywords/interpolated-strings.md)功能。</span><span class="sxs-lookup"><span data-stu-id="c3cbd-108">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3cbd-109">範例</span><span class="sxs-lookup"><span data-stu-id="c3cbd-109">Example</span></span>  
 <span data-ttu-id="c3cbd-110">[!code-cs[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c3cbd-110">[!code-cs[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]</span></span>  
  
 <span data-ttu-id="c3cbd-111">這些範例全都會將字串常值寫入至檔案，不過您可能比較想要使用 <xref:System.String.Format%2A> 方法，該方法提供許多控制項讓您撰寫不同類型的值，在欄位中靠右或靠左對齊、使用或不使用邊框間距等等。</span><span class="sxs-lookup"><span data-stu-id="c3cbd-111">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="c3cbd-112">您也可以使用 C# [字串插值](../../../csharp/language-reference/keywords/interpolated-strings.md)功能。</span><span class="sxs-lookup"><span data-stu-id="c3cbd-112">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c3cbd-113">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="c3cbd-113">Robust Programming</span></span>  
 <span data-ttu-id="c3cbd-114">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="c3cbd-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="c3cbd-115">該檔案存在而且是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="c3cbd-115">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="c3cbd-116">路徑名稱可能太長。</span><span class="sxs-lookup"><span data-stu-id="c3cbd-116">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="c3cbd-117">磁碟可能已滿。</span><span class="sxs-lookup"><span data-stu-id="c3cbd-117">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3cbd-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3cbd-118">See Also</span></span>  
 <span data-ttu-id="c3cbd-119">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c3cbd-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="c3cbd-120"> [檔案系統和登錄 (C# 程式設計手冊)](../../../csharp/programming-guide/file-system/index.md) </span><span class="sxs-lookup"><span data-stu-id="c3cbd-120"> [File System and the Registry (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md) </span></span>  
<span data-ttu-id="c3cbd-121"> [範例：如何將集合儲存至應用程式儲存空間](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)</span><span class="sxs-lookup"><span data-stu-id="c3cbd-121"> [Sample: Save a collection to Application Storage](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)</span></span>
