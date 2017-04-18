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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2e58363369ae4420879310bf09ed89cdd4f5b5cc
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a>如何︰ 判斷檔案是否為組件 (Visual Basic)
檔案是組件，若它 managed，而且包含組件中的項目及其中繼資料。 如需有關組件和中繼資料的詳細資訊，請參閱主題[組件資訊清單](https://msdn.microsoft.com/library/1w45z383)。  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>如何以手動方式判斷檔案是否為組件  
  
1.  啟動[Ildasm.exe （IL 反組譯工具）](https://msdn.microsoft.com/library/f7dy01k1)。  
  
2.  載入您想要測試的檔案。  
  
3.  如果**ILDASM** ，檔案不是可移植執行檔 (PE) 檔案，則不是組件的報表。 如需詳細資訊，請參閱主題[How to︰ 檢視組件內容](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709)。  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>如何以程式設計方式判斷檔案是否為組件  
  
1.  呼叫<xref:System.Reflection.AssemblyName.GetAssemblyName%2A>方法，傳遞您要測試的檔案名稱與完整檔案路徑。</xref:System.Reflection.AssemblyName.GetAssemblyName%2A>  
  
2.  如果<xref:System.BadImageFormatException>擲回例外狀況，檔案不是組件。</xref:System.BadImageFormatException>  
  
## <a name="example"></a>範例  
 這個範例會測試 DLL，查看它是否為組件。  
  
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
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>方法會載入測試檔案，並在讀取的資訊之後再釋放。</xref:System.Reflection.AssemblyName.GetAssemblyName%2A>  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName>   
 [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)   
 [組件和全域組件快取 (Visual Basic)](index.md)
