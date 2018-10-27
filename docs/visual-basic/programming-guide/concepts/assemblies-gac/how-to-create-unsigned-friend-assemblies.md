---
title: 如何： 建立未簽署的 Friend 組件 (Visual Basic)
ms.date: 03/14/2018
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
ms.openlocfilehash: 5fb2310a5d883e65df0b59b6fe316aa4d4637b7f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188314"
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>如何： 建立未簽署的 Friend 組件 (Visual Basic)
此範例示範如何搭配未簽署的組件使用 friend 組件。  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>建立組件和 friend 組件  
  
1.  開啟命令提示字元。  
  
2.  建立名為 Visual Basic 檔案`friend_signed_A.`包含下列程式碼。 程式碼會使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性宣告 friend_signed_B 為 Friend 組件。  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' vbc -target:library friend_unsigned_A.vb  
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
  
3.  使用下列命令來編譯及簽署 friend_signed_A。  
  
    ```console  
    vbc -target:library friend_unsigned_A.vb  
    ```  
  
4.  建立名為 Visual Basic 檔案`friend_unsigned_B`包含下列程式碼。 因為 friend_unsigned_A 會將 friend_unsigned_B 指定為 friend 組件，所以 friend_unsigned_B 中的程式碼可以存取 friend_unsigned_A 中的 `Friend` 類型和成員。  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
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
  
    ```console
    vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱。 您可以使用，以明確地設定組件`/out`編譯器選項。  
  
6.  執行 friend_signed_B.exe 檔案。  
  
     此程式會顯示兩個字串:"Class1.Test"和"Class2.Test"。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似性。 主要差異是 <xref:System.Security.Permissions.StrongNameIdentityPermission> 可以要求安全性權限執行特定的程式碼區段，而 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性則是控制 `Friend` 類型和成員的可見性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [如何： 建立簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [程式設計指南概念](../../../../visual-basic/programming-guide/concepts/index.md)
