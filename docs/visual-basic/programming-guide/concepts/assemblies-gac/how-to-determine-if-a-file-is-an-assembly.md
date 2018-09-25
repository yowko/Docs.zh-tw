---
title: 如何： 判斷檔案是否為組件 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
ms.openlocfilehash: ced41279e7e192d6d5bed53dbce7378395b32e6d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47089395"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a><span data-ttu-id="5b716-102">如何： 判斷檔案是否為組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b716-102">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>
<span data-ttu-id="5b716-103">檔案只有受管理時才是組件，而且其中繼資料會包含組件項目。</span><span class="sxs-lookup"><span data-stu-id="5b716-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="5b716-104">如需組件和中繼資料的詳細資訊，請參閱[組件資訊清單](../../../../framework/app-domains/assembly-manifest.md)主題。</span><span class="sxs-lookup"><span data-stu-id="5b716-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../framework/app-domains/assembly-manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="5b716-105">如何以手動方式判斷檔案是否為組件</span><span class="sxs-lookup"><span data-stu-id="5b716-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="5b716-106">啟動 [Ildasm.exe (IL 反組譯工具)](../../../../framework/tools/ildasm-exe-il-disassembler.md)。</span><span class="sxs-lookup"><span data-stu-id="5b716-106">Start the [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2.  <span data-ttu-id="5b716-107">載入要測試的檔案。</span><span class="sxs-lookup"><span data-stu-id="5b716-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="5b716-108">如果 **ILDASM** 回報該檔案並非可攜式執行檔 (PE)，則檔案不是組件。</span><span class="sxs-lookup"><span data-stu-id="5b716-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="5b716-109">如需詳細資訊，請參閱[如何：檢視組件內容](../../../../framework/app-domains/how-to-view-assembly-contents.md)主題。</span><span class="sxs-lookup"><span data-stu-id="5b716-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="5b716-110">如何以程式設計方式判斷檔案是否為組件</span><span class="sxs-lookup"><span data-stu-id="5b716-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="5b716-111">呼叫 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法，並傳遞您要測試之檔案的完整檔案路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="5b716-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="5b716-112">如果擲回 <xref:System.BadImageFormatException> 例外狀況，則檔案不是組件。</span><span class="sxs-lookup"><span data-stu-id="5b716-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b716-113">範例</span><span class="sxs-lookup"><span data-stu-id="5b716-113">Example</span></span>  
 <span data-ttu-id="5b716-114">此範例會測試一個 DLL 以查看其是否為組件。</span><span class="sxs-lookup"><span data-stu-id="5b716-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="5b716-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法會載入測試檔案，然後在讀取資訊之後釋放它。</span><span class="sxs-lookup"><span data-stu-id="5b716-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b716-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b716-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>  
- [<span data-ttu-id="5b716-117">程式設計概念</span><span class="sxs-lookup"><span data-stu-id="5b716-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
- [<span data-ttu-id="5b716-118">組件和全域組件快取 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b716-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](index.md)
