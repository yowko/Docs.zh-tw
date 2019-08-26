---
title: 作法：一次一行讀取文字檔 (Visual C#)
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 75274d93ee29feb5f79dfc29c24109f25fd98a5c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589957"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a><span data-ttu-id="43b1a-102">作法：一次一行讀取文字檔 (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="43b1a-102">How to: Read a Text File One Line at a Time (Visual C#)</span></span>
<span data-ttu-id="43b1a-103">此範例會使用 `StreamReader` 類別的 `ReadLine` 方法，將文字檔的內容一次一行讀入字串中。</span><span class="sxs-lookup"><span data-stu-id="43b1a-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="43b1a-104">每個文字行都會儲存到字串 `line` 中並顯示在畫面上。</span><span class="sxs-lookup"><span data-stu-id="43b1a-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43b1a-105">範例</span><span class="sxs-lookup"><span data-stu-id="43b1a-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="43b1a-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="43b1a-106">Compiling the Code</span></span>  
 <span data-ttu-id="43b1a-107">將程式碼複製並貼到主控台應用程式的 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="43b1a-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="43b1a-108">以實際檔案名稱取代 `"c:\test.txt"`。</span><span class="sxs-lookup"><span data-stu-id="43b1a-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="43b1a-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="43b1a-109">Robust Programming</span></span>  
 <span data-ttu-id="43b1a-110">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="43b1a-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="43b1a-111">檔案可能不存在。</span><span class="sxs-lookup"><span data-stu-id="43b1a-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="43b1a-112">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="43b1a-112">.NET Framework Security</span></span>  
 <span data-ttu-id="43b1a-113">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="43b1a-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="43b1a-114">例如，`myFile.cs` 檔案可能不是 C# 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="43b1a-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b1a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43b1a-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="43b1a-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="43b1a-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="43b1a-117">檔案系統和登錄 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="43b1a-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
