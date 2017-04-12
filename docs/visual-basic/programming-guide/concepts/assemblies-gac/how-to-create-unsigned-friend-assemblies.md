---
title: "如何︰ 建立未簽署的 Friend 組件 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ceddb35c306f72c8927deda326d9fcca6c75d786
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>如何︰ 建立未簽署的 Friend 組件 (Visual Basic)
這個範例示範如何使用 friend 組件未簽署的組件。  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>若要建立組件和 friend 組件  
  
1.  開啟命令提示字元。  
  
2.  建立名為 Visual Basic 檔案`friend_signed_A.`，其中包含下列程式碼。 程式碼使用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性宣告為 friend 組件 friend_signed_B。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' Vbc /target:library friend_unsigned_A.vb  
    Imports System.Runtime.CompilerServices  
    Imports System  
  
    <Assembly: InternalsVisibleTo("friend_unsigned_B")>   
  
    ' Friend type.  
    Friend Class Class1  
        Public Sub Test()  
            Console.WriteLine("Class1.Test")  
        End Sub  
    End Class  
  
    ' Public type with Friend member.  
    Public Class Class2  
        Friend Sub Test()  
            Console.WriteLine("Class2.Test")  
        End Sub  
    End Class  
    ```  
  
3.  編譯並使用下列命令來簽署 friend_signed_A。  
  
    ```vb  
    Vbc /target:library friend_unsigned_A.vb  
    ```  
  
4.  建立名為 Visual Basic 檔案`friend_unsigned_B`，其中包含下列程式碼。 由於 friend_unsigned_A 做為 friend 組件指定 friend_unsigned_B friend_unsigned_B 中的程式碼可以存取`Friend`型別和從 friend_unsigned_A 的成員。  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    Module Module1  
        Sub Main()  
            ' Access a Friend type.  
            Dim inst1 As New Class1()  
            inst1.Test()  
  
            Dim inst2 As New Class2()  
            ' Access a Friend member of a public type.  
            inst2.Test()  
  
            System.Console.ReadLine()  
        End Sub  
    End Module  
    ```  
  
5.  使用下列命令來編譯 friend_signed_B。  
  
    ```vb  
    Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     由編譯器產生的組件名稱必須符合 friend 組件名稱傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 您可以使用，以明確地設定組件`/out`編譯器選項。  
  
6.  執行 friend_signed_B.exe 檔案。  
  
     程式會列印兩個字串: 「 Class1.Test 」 和 「 Class2.Test 」。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性和<xref:System.Security.Permissions.StrongNameIdentityPermission>類別</xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>之間有相似之處 主要差異在於<xref:System.Security.Permissions.StrongNameIdentityPermission>可以要求安全性權限才能執行特定程式碼，而<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性控制的可視性`Friend`型別和成員。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> </xref:System.Security.Permissions.StrongNameIdentityPermission>  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [如何︰ 建立已簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [程式設計指南概念](../../../../visual-basic/programming-guide/concepts/index.md)
