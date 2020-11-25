---
title: 如何：判斷檔案是否為元件
description: 本文說明如何以手動和程式設計方式判斷檔案是否為 .NET 元件。
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: b78acaad31996f8fc2b965f51f541e99aeceb111
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731497"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="8b0e6-103">如何：判斷檔案是否為元件</span><span class="sxs-lookup"><span data-stu-id="8b0e6-103">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="8b0e6-104">檔案只有受管理時才是組件，而且其中繼資料會包含組件項目。</span><span class="sxs-lookup"><span data-stu-id="8b0e6-104">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="8b0e6-105">如需元件和中繼資料的詳細資訊，請參閱 [組件資訊清單](manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="8b0e6-105">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="8b0e6-106">如何以手動方式判斷檔案是否為組件</span><span class="sxs-lookup"><span data-stu-id="8b0e6-106">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="8b0e6-107">啟動 [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md)。</span><span class="sxs-lookup"><span data-stu-id="8b0e6-107">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="8b0e6-108">載入您想要測試的檔案。</span><span class="sxs-lookup"><span data-stu-id="8b0e6-108">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="8b0e6-109">如果 **ILDASM** 回報該檔案並非可攜式執行檔 (PE)，則檔案不是組件。</span><span class="sxs-lookup"><span data-stu-id="8b0e6-109">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="8b0e6-110">如需詳細資訊，請參閱主題 [如何：查看元件內容](view-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="8b0e6-110">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="8b0e6-111">如何以程式設計方式判斷檔案是否為組件</span><span class="sxs-lookup"><span data-stu-id="8b0e6-111">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="8b0e6-112">呼叫 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> 方法，並傳遞您要測試之檔案的完整檔案路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="8b0e6-112">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="8b0e6-113">如果擲回 <xref:System.BadImageFormatException> 例外狀況，則檔案不是組件。</span><span class="sxs-lookup"><span data-stu-id="8b0e6-113">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b0e6-114">範例</span><span class="sxs-lookup"><span data-stu-id="8b0e6-114">Example</span></span>  

<span data-ttu-id="8b0e6-115">此範例會測試一個 DLL 以查看其是否為組件。</span><span class="sxs-lookup"><span data-stu-id="8b0e6-115">This example tests a DLL to see if it is an assembly.</span></span>  

```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  

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

<span data-ttu-id="8b0e6-116"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法會載入測試檔案，然後在讀取資訊之後釋放它。</span><span class="sxs-lookup"><span data-stu-id="8b0e6-116">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b0e6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b0e6-117">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="8b0e6-118">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="8b0e6-118">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8b0e6-119"> (Visual Basic) 的程式設計概念 </span><span class="sxs-lookup"><span data-stu-id="8b0e6-119">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="8b0e6-120">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="8b0e6-120">Assemblies in .NET</span></span>](index.md)
