---
title: '如何一次一行讀取文字檔-c # 程式設計手冊'
description: 瞭解如何一次一行讀取文字檔。 查看程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 1e29013b1008e1000c23804dc3056014cc7c104b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301953"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="d98a7-104">如何一次一行讀取文字檔（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="d98a7-104">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="d98a7-105">此範例會使用 `StreamReader` 類別的 `ReadLine` 方法，將文字檔的內容一次一行讀入字串中。</span><span class="sxs-lookup"><span data-stu-id="d98a7-105">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="d98a7-106">每個文字行都會儲存到字串 `line` 中並顯示在畫面上。</span><span class="sxs-lookup"><span data-stu-id="d98a7-106">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d98a7-107">範例</span><span class="sxs-lookup"><span data-stu-id="d98a7-107">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="d98a7-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d98a7-108">Compiling the Code</span></span>  
 <span data-ttu-id="d98a7-109">將程式碼複製並貼到主控台應用程式的 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="d98a7-109">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="d98a7-110">以實際檔案名稱取代 `"c:\test.txt"`。</span><span class="sxs-lookup"><span data-stu-id="d98a7-110">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d98a7-111">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="d98a7-111">Robust Programming</span></span>  
 <span data-ttu-id="d98a7-112">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="d98a7-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d98a7-113">檔案可能不存在。</span><span class="sxs-lookup"><span data-stu-id="d98a7-113">The file may not exist.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="d98a7-114">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="d98a7-114">.NET Security</span></span>  
 <span data-ttu-id="d98a7-115">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="d98a7-115">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="d98a7-116">例如，`myFile.cs` 檔案可能不是 C# 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="d98a7-116">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d98a7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d98a7-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="d98a7-118">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d98a7-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d98a7-119">檔案系統和登錄 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d98a7-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
