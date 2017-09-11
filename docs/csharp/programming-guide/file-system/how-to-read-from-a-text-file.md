---
title: "如何：從文字檔讀取 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- StreamReader.ReadToEnd
dev_langs:
- CSharp
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
caps.latest.revision: 17
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
ms.openlocfilehash: d545aa7f25da49b3ca0fc50b0c5a55c9c0d2b967
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="59ac4-102">如何：從文字檔讀取 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="59ac4-102">How to: Read From a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="59ac4-103">此範例使用 <xref:System.IO.File?displayProperty=fullName> 類別中的靜態方法 <xref:System.IO.File.ReadAllText%2A> 和 <xref:System.IO.File.ReadAllLines%2A> 來讀取文字檔的內容。</span><span class="sxs-lookup"><span data-stu-id="59ac4-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=fullName> class.</span></span>  
  
 <span data-ttu-id="59ac4-104">如需使用 <xref:System.IO.StreamReader> 的範例，請參閱[如何：一次一行讀取文字檔](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)。</span><span class="sxs-lookup"><span data-stu-id="59ac4-104">For an example that uses <xref:System.IO.StreamReader>, see [How to: Read a Text File One Line at a Time](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59ac4-105">此範例中所用的檔案是在[如何︰寫入文字檔](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)主題中建立。</span><span class="sxs-lookup"><span data-stu-id="59ac4-105">The files that are used in this example are created in the topic [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59ac4-106">範例</span><span class="sxs-lookup"><span data-stu-id="59ac4-106">Example</span></span>  
 <span data-ttu-id="59ac4-107">[!code-cs[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="59ac4-107">[!code-cs[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59ac4-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="59ac4-108">Compiling the Code</span></span>  
 <span data-ttu-id="59ac4-109">將程式碼複製並貼到 C# 主控台應用程式中。</span><span class="sxs-lookup"><span data-stu-id="59ac4-109">Copy the code and paste it into a C# console application.</span></span>  
  
 <span data-ttu-id="59ac4-110">如果您不想使用[如何︰寫入文字檔](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)中的文字檔，請以您電腦上的適當路徑和檔案名稱取代 `ReadAllText` 和 `ReadAllLines` 的引數。</span><span class="sxs-lookup"><span data-stu-id="59ac4-110">If you are not using the text files from [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="59ac4-111">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="59ac4-111">Robust Programming</span></span>  
 <span data-ttu-id="59ac4-112">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="59ac4-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="59ac4-113">檔案不存在或不在指定的位置。</span><span class="sxs-lookup"><span data-stu-id="59ac4-113">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="59ac4-114">請檢查路徑和檔案名稱的拼字。</span><span class="sxs-lookup"><span data-stu-id="59ac4-114">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="59ac4-115">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="59ac4-115">.NET Framework Security</span></span>  
 <span data-ttu-id="59ac4-116">請勿依賴檔案的名稱來判斷檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="59ac4-116">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="59ac4-117">例如，`myFile.cs` 檔案可能不是 C# 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="59ac4-117">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ac4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59ac4-118">See Also</span></span>  
 <span data-ttu-id="59ac4-119"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="59ac4-119"><xref:System.IO?displayProperty=fullName></span></span>   
<span data-ttu-id="59ac4-120"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="59ac4-120"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="59ac4-121"> [檔案系統和登錄 (C# 程式設計手冊)](../../../csharp/programming-guide/file-system/index.md)</span><span class="sxs-lookup"><span data-stu-id="59ac4-121"> [File System and the Registry (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)</span></span>
