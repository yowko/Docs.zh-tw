---
title: 如何：判斷檔案是否為組件 (C#)
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: ee2313677fba21624ccdb44db779633f6c4503bf
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861006"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a><span data-ttu-id="31432-102">如何：判斷檔案是否為組件 (C#)</span><span class="sxs-lookup"><span data-stu-id="31432-102">How to: Determine If a File Is an Assembly (C#)</span></span>
<span data-ttu-id="31432-103">檔案只有受管理時才是組件，而且其中繼資料會包含組件項目。</span><span class="sxs-lookup"><span data-stu-id="31432-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="31432-104">如需組件和中繼資料的詳細資訊，請參閱[組件資訊清單](../../../../../docs/framework/app-domains/assembly-manifest.md)主題。</span><span class="sxs-lookup"><span data-stu-id="31432-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../../docs/framework/app-domains/assembly-manifest.md).</span></span>  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="31432-105">如何以手動方式判斷檔案是否為組件</span><span class="sxs-lookup"><span data-stu-id="31432-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="31432-106">啟動 [Ildasm.exe (IL 反組譯工具)](../../../../framework/tools/ildasm-exe-il-disassembler.md)。</span><span class="sxs-lookup"><span data-stu-id="31432-106">Start the [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2.  <span data-ttu-id="31432-107">載入要測試的檔案。</span><span class="sxs-lookup"><span data-stu-id="31432-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="31432-108">如果 **ILDASM** 回報該檔案並非可攜式執行檔 (PE)，則檔案不是組件。</span><span class="sxs-lookup"><span data-stu-id="31432-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="31432-109">如需詳細資訊，請參閱[如何：檢視組件內容](../../../../framework/app-domains/how-to-view-assembly-contents.md)主題。</span><span class="sxs-lookup"><span data-stu-id="31432-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="31432-110">如何以程式設計方式判斷檔案是否為組件</span><span class="sxs-lookup"><span data-stu-id="31432-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="31432-111">呼叫 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法，並傳遞您要測試之檔案的完整檔案路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="31432-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="31432-112">如果擲回 <xref:System.BadImageFormatException> 例外狀況，則檔案不是組件。</span><span class="sxs-lookup"><span data-stu-id="31432-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31432-113">範例</span><span class="sxs-lookup"><span data-stu-id="31432-113">Example</span></span>  
 <span data-ttu-id="31432-114">此範例會測試一個 DLL 以查看其是否為組件。</span><span class="sxs-lookup"><span data-stu-id="31432-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
```  
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
  
 <span data-ttu-id="31432-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法會載入測試檔案，然後在讀取資訊之後釋放它。</span><span class="sxs-lookup"><span data-stu-id="31432-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31432-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="31432-116">See Also</span></span>

- <xref:System.Reflection.AssemblyName>  
- [<span data-ttu-id="31432-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="31432-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="31432-118">組件和全域組件快取 (C#)</span><span class="sxs-lookup"><span data-stu-id="31432-118">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
