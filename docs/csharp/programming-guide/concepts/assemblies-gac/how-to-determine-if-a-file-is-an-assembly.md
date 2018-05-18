---
title: 如何：判斷檔案是否為組件 (C#)
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: 0557f42d42e42606c3d1b2a2ad71bd797a159e8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>如何：判斷檔案是否為組件 (C#)
檔案只有受管理時才是組件，而且其中繼資料會包含組件項目。 如需組件和中繼資料的詳細資訊，請參閱[組件資訊清單](../../../../../docs/framework/app-domains/assembly-manifest.md)主題。  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>如何以手動方式判斷檔案是否為組件  
  
1.  啟動 [Ildasm.exe (IL 反組譯工具)](https://msdn.microsoft.com/library/f7dy01k1)。  
  
2.  載入要測試的檔案。  
  
3.  如果 **ILDASM** 回報該檔案並非可攜式執行檔 (PE)，則檔案不是組件。 如需詳細資訊，請參閱[如何：檢視組件內容](../../../../framework/app-domains/how-to-view-assembly-contents.md)主題。  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>如何以程式設計方式判斷檔案是否為組件  
  
1.  呼叫 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法，並傳遞您要測試之檔案的完整檔案路徑和名稱。  
  
2.  如果擲回 <xref:System.BadImageFormatException> 例外狀況，則檔案不是組件。  
  
## <a name="example"></a>範例  
 此範例會測試一個 DLL 以查看其是否為組件。  
  
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
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法會載入測試檔案，然後在讀取資訊之後釋放它。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Reflection.AssemblyName>  
 [C# 程式設計指南](../../../../csharp/programming-guide/index.md)  
 [組件和全域組件快取 (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
