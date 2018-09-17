---
title: 如何： 判斷檔案是否為組件 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
ms.openlocfilehash: ced41279e7e192d6d5bed53dbce7378395b32e6d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45745587"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a>如何： 判斷檔案是否為組件 (Visual Basic)
檔案只有受管理時才是組件，而且其中繼資料會包含組件項目。 如需組件和中繼資料的詳細資訊，請參閱[組件資訊清單](../../../../framework/app-domains/assembly-manifest.md)主題。  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>如何以手動方式判斷檔案是否為組件  
  
1.  啟動 [Ildasm.exe (IL 反組譯工具)](../../../../framework/tools/ildasm-exe-il-disassembler.md)。  
  
2.  載入要測試的檔案。  
  
3.  如果 **ILDASM** 回報該檔案並非可攜式執行檔 (PE)，則檔案不是組件。 如需詳細資訊，請參閱[如何：檢視組件內容](../../../../framework/app-domains/how-to-view-assembly-contents.md)主題。  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>如何以程式設計方式判斷檔案是否為組件  
  
1.  呼叫 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法，並傳遞您要測試之檔案的完整檔案路徑和名稱。  
  
2.  如果擲回 <xref:System.BadImageFormatException> 例外狀況，則檔案不是組件。  
  
## <a name="example"></a>範例  
 此範例會測試一個 DLL 以查看其是否為組件。  
  
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
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法會載入測試檔案，然後在讀取資訊之後釋放它。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.AssemblyName>  
- [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)  
- [組件和全域組件快取 (Visual Basic)](index.md)
