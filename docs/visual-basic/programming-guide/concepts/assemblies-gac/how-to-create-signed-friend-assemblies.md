---
title: "如何︰ 建立已簽署的 Friend 組件 (Visual Basic) |Microsoft 文件"
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
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1a69f7e833800ec7417bc35fad763f1001b3e7f9
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a>如何︰ 建立已簽署的 Friend 組件 (Visual Basic)
這個範例示範如何使用 friend 組件具有強式名稱的組件。 這兩個組件必須使用強式名稱。 雖然這兩個組件，在此範例中使用相同的金鑰，您可以使用不同的索引鍵的兩個組件。  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>若要建立簽署的組件和 friend 組件  
  
1.  開啟命令提示字元。  
  
2.  產生金鑰檔，並顯示它的公開金鑰，則您可以使用強式名稱工具以下的命令順序。 如需詳細資訊，請參閱 [Sn.exe (強式名稱工具)](https://msdn.microsoft.com/library/k5b5tt23)。  
  
    1.  產生強式名稱金鑰，此範例中，並將它儲存在檔案 FriendAssemblies.snk:  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  從 FriendAssemblies.snk 擷取公開金鑰，並將它放入 FriendAssemblies.publickey:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  顯示儲存在檔案 FriendAssemblies.publickey 的公開金鑰︰  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  建立名為 Visual Basic 檔案`friend_signed_A`，其中包含下列程式碼。 程式碼使用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性宣告為 friend 組件 friend_signed_B。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
  
     強式名稱工具會在每次執行時產生新的公開金鑰。 因此，您必須取代下列程式碼中的公開金鑰您剛產生的公開金鑰，如下列範例所示。  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4.  編譯並使用下列命令來簽署 friend_signed_A。  
  
    ```vb  
    Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  建立名為 Visual Basic 檔案`friend_signed_B`且包含下列程式碼。 由於 friend_signed_A 做為 friend 組件指定 friend_signed_B friend_signed_B 中的程式碼可以存取`Friend`型別和從 friend_signed_A 的成員。 此檔案包含下列程式碼。  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6.  編譯並使用下列命令來簽署 friend_signed_B。  
  
    ```vb  
    Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     由編譯器所產生的組件的名稱必須符合 friend 組件名稱傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 您可以使用，以明確地設定組件`/out`編譯器選項。 如需詳細資訊，請參閱[/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)。  
  
7.  執行 friend_signed_B.exe 檔案。  
  
     程式會列印"Class1.Test"的字串。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性和<xref:System.Security.Permissions.StrongNameIdentityPermission>類別</xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>之間有相似之處 主要差異在於<xref:System.Security.Permissions.StrongNameIdentityPermission>可以要求安全性權限才能執行特定程式碼，而<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性控制的可視性`Friend`型別和成員。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> </xref:System.Security.Permissions.StrongNameIdentityPermission>  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [如何︰ 建立未簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)   
 [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [Sn.exe （強式名稱工具）](https://msdn.microsoft.com/library/k5b5tt23)   
 [建立和使用強式名稱組件](https://msdn.microsoft.com/library/xwb8f617)   
 [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)
