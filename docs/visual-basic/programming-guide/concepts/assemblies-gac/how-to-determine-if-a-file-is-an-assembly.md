---
title: "如何︰ 判斷檔案是否為組件 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4bd3404cbdc3b79ff92290a53574080bf197fe9d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a><span data-ttu-id="c96bc-102">如何︰ 判斷檔案是否為組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c96bc-102">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>
<span data-ttu-id="c96bc-103">檔案是組件，若它 managed，而且包含組件中的項目及其中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c96bc-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="c96bc-104">如需有關組件和中繼資料的詳細資訊，請參閱主題[組件資訊清單](https://msdn.microsoft.com/library/1w45z383)。</span><span class="sxs-lookup"><span data-stu-id="c96bc-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](https://msdn.microsoft.com/library/1w45z383).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="c96bc-105">如何以手動方式判斷檔案是否為組件</span><span class="sxs-lookup"><span data-stu-id="c96bc-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="c96bc-106">啟動[Ildasm.exe （IL 反組譯工具）](https://msdn.microsoft.com/library/f7dy01k1)。</span><span class="sxs-lookup"><span data-stu-id="c96bc-106">Start the [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span></span>  
  
2.  <span data-ttu-id="c96bc-107">載入您想要測試的檔案。</span><span class="sxs-lookup"><span data-stu-id="c96bc-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="c96bc-108">如果**ILDASM** ，檔案不是可移植執行檔 (PE) 檔案，則不是組件的報表。</span><span class="sxs-lookup"><span data-stu-id="c96bc-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="c96bc-109">如需詳細資訊，請參閱主題[How to︰ 檢視組件內容](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709)。</span><span class="sxs-lookup"><span data-stu-id="c96bc-109">For more information, see the topic [How to: View Assembly Contents](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="c96bc-110">如何以程式設計方式判斷檔案是否為組件</span><span class="sxs-lookup"><span data-stu-id="c96bc-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="c96bc-111">呼叫<xref:System.Reflection.AssemblyName.GetAssemblyName%2A>方法，傳遞您要測試的檔案名稱與完整檔案路徑。</xref:System.Reflection.AssemblyName.GetAssemblyName%2A></span><span class="sxs-lookup"><span data-stu-id="c96bc-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="c96bc-112">如果<xref:System.BadImageFormatException>擲回例外狀況，檔案不是組件。</xref:System.BadImageFormatException></span><span class="sxs-lookup"><span data-stu-id="c96bc-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c96bc-113">範例</span><span class="sxs-lookup"><span data-stu-id="c96bc-113">Example</span></span>  
 <span data-ttu-id="c96bc-114">這個範例會測試 DLL，查看它是否為組件。</span><span class="sxs-lookup"><span data-stu-id="c96bc-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="c96bc-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A>方法會載入測試檔案，並在讀取的資訊之後再釋放。</xref:System.Reflection.AssemblyName.GetAssemblyName%2A></span><span class="sxs-lookup"><span data-stu-id="c96bc-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c96bc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c96bc-116">See Also</span></span>  
 <span data-ttu-id="c96bc-117"><xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName></span><span class="sxs-lookup"><span data-stu-id="c96bc-117"><xref:System.Reflection.AssemblyName></span></span>   
<span data-ttu-id="c96bc-118"> [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="c96bc-118"> [Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="c96bc-119"> [組件和全域組件快取 (Visual Basic)](index.md)</span><span class="sxs-lookup"><span data-stu-id="c96bc-119"> [Assemblies and the Global Assembly Cache (Visual Basic)](index.md)</span></span>
