---
title: HOW TO：建立簽署的 Friend 組件 (Visual Basic)
ms.date: 03/14/2018
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
ms.openlocfilehash: 4ff32015647a565f7f68e944ae028deb7f738e28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022268"
---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a>HOW TO：建立簽署的 Friend 組件 (Visual Basic)
此範例示範如何搭配具有強式名稱的組件使用 friend 組件。 這兩個組件都必須具有強式名稱。 雖然此範例中的兩個組件使用相同的金鑰，但您可以針對這兩個組件使用不同的金鑰。  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>建立簽署的組件和 friend 組件  
  
1. 開啟命令提示字元。  
  
2. 使用下列命令順序和強式名稱工具，產生金鑰檔並顯示其公開金鑰。 如需詳細資訊，請參閱 < [Sn.exe （強式名稱工具）](../../../../framework/tools/sn-exe-strong-name-tool.md))。  
  
    1. 為此範例產生強式名稱金鑰，然後將它儲存在 FriendAssemblies.snk 檔案中：  
  
         `sn -k FriendAssemblies.snk`  
  
    2. 從 FriendAssemblies.snk 擷取公開金鑰，然後將它放入 FriendAssemblies.publickey：  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. 顯示儲存在 FriendAssemblies.publickey 檔案中的公開金鑰：  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. 建立名為 Visual Basic 檔案`friend_signed_A`包含下列程式碼。 程式碼會使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性宣告 friend_signed_B 為 Friend 組件。  
  
     強式名稱工具會在每次執行時產生新的公開金鑰。 因此，您必須將下列程式碼中的公開金鑰取代為剛產生的公開金鑰，如下列範例所示。  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4. 使用下列命令來編譯及簽署 friend_signed_A。  
  
    ```console  
    Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5. 建立 Visual Basic 檔案，稱為`friend_signed_B`並包含下列程式碼。 因為 friend_signed_A 會將 friend_signed_B 指定為 friend 組件，所以 friend_signed_B 中的程式碼可以存取 friend_signed_A 中的 `Friend` 類型和成員。 該檔案包含下列程式碼。  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6. 使用下列命令來編譯及簽署 friend_signed_B。  
  
    ```console  
    vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱。 您可以使用，以明確地設定組件`-out`編譯器選項。 如需詳細資訊，請參閱 < [-(Visual basic)](../../../../visual-basic/reference/command-line-compiler/out.md)。  
  
7. 執行 friend_signed_B.exe 檔案。  
  
     此程式會顯示字串"Class1.Test"。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似性。 主要差異是 <xref:System.Security.Permissions.StrongNameIdentityPermission> 可以要求安全性權限執行特定的程式碼區段，而 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性則是控制 `Friend` 類型和成員的可見性。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET 中的組件](../../../../standard/assembly/index.md)
- [Friend 組件](../../../../standard/assembly/friend-assemblies.md)
- [如何：建立未簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [-keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Sn.exe （強式名稱工具）](../../../../framework/tools/sn-exe-strong-name-tool.md))
- [建立和使用強式名稱的組件](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)
- [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)
