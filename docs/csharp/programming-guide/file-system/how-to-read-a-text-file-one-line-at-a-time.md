---
title: '如何一次一行讀取文字檔-c # 程式設計手冊'
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: b54d072ce9837f9b15694f2d7100817de62e9762
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241769"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="cdf05-102">如何一次一行讀取文字檔（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="cdf05-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="cdf05-103">此範例會使用 `StreamReader` 類別的 `ReadLine` 方法，將文字檔的內容一次一行讀入字串中。</span><span class="sxs-lookup"><span data-stu-id="cdf05-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="cdf05-104">每個文字行都會儲存到字串 `line` 中並顯示在畫面上。</span><span class="sxs-lookup"><span data-stu-id="cdf05-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdf05-105">範例</span><span class="sxs-lookup"><span data-stu-id="cdf05-105">Example</span></span>  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cdf05-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="cdf05-106">Compiling the Code</span></span>  
 <span data-ttu-id="cdf05-107">將程式碼複製並貼到主控台應用程式的 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="cdf05-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="cdf05-108">以實際檔案名稱取代 `"c:\test.txt"`。</span><span class="sxs-lookup"><span data-stu-id="cdf05-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cdf05-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="cdf05-109">Robust Programming</span></span>  
 <span data-ttu-id="cdf05-110">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="cdf05-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="cdf05-111">檔案可能不存在。</span><span class="sxs-lookup"><span data-stu-id="cdf05-111">The file may not exist.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="cdf05-112">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="cdf05-112">.NET Security</span></span>  
 <span data-ttu-id="cdf05-113">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="cdf05-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="cdf05-114">例如，`myFile.cs` 檔案可能不是 C# 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="cdf05-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf05-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdf05-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="cdf05-116">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cdf05-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cdf05-117">檔案系統和登錄 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="cdf05-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
