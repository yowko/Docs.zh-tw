---
title: "如何： 判斷檔案是否為組件 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 314c65ebfbb2aaf1acc9fad4cefa13c5f4f17cec
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a><span data-ttu-id="a8785-102">如何： 判斷檔案是否為組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8785-102">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>
<span data-ttu-id="a8785-103">檔案只有受管理時才是組件，而且其中繼資料會包含組件項目。</span><span class="sxs-lookup"><span data-stu-id="a8785-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="a8785-104">如需組件和中繼資料的詳細資訊，請參閱[組件資訊清單](../../../../../docs/framework/app-domains/assembly-manifest.md)主題。</span><span class="sxs-lookup"><span data-stu-id="a8785-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../../docs/framework/app-domains/assembly-manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="a8785-105">如何以手動方式判斷檔案是否為組件</span><span class="sxs-lookup"><span data-stu-id="a8785-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="a8785-106">啟動 [Ildasm.exe (IL 反組譯工具)](https://msdn.microsoft.com/library/f7dy01k1)。</span><span class="sxs-lookup"><span data-stu-id="a8785-106">Start the [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span></span>  
  
2.  <span data-ttu-id="a8785-107">載入要測試的檔案。</span><span class="sxs-lookup"><span data-stu-id="a8785-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="a8785-108">如果 **ILDASM** 回報該檔案並非可攜式執行檔 (PE)，則檔案不是組件。</span><span class="sxs-lookup"><span data-stu-id="a8785-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="a8785-109">如需詳細資訊，請參閱[如何：檢視組件內容](../../../../framework/app-domains/how-to-view-assembly-contents.md)主題。</span><span class="sxs-lookup"><span data-stu-id="a8785-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="a8785-110">如何以程式設計方式判斷檔案是否為組件</span><span class="sxs-lookup"><span data-stu-id="a8785-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="a8785-111">呼叫 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法，並傳遞您要測試之檔案的完整檔案路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="a8785-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="a8785-112">如果擲回 <xref:System.BadImageFormatException> 例外狀況，則檔案不是組件。</span><span class="sxs-lookup"><span data-stu-id="a8785-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8785-113">範例</span><span class="sxs-lookup"><span data-stu-id="a8785-113">Example</span></span>  
 <span data-ttu-id="a8785-114">此範例會測試一個 DLL 以查看其是否為組件。</span><span class="sxs-lookup"><span data-stu-id="a8785-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```
  
 <span data-ttu-id="a8785-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法會載入測試檔案，然後在讀取資訊之後釋放它。</span><span class="sxs-lookup"><span data-stu-id="a8785-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8785-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8785-116">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="a8785-117">程式設計概念</span><span class="sxs-lookup"><span data-stu-id="a8785-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="a8785-118">組件和全域組件快取 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8785-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](index.md)
