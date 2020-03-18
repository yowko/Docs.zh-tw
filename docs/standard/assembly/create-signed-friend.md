---
title: 如何：創建簽名的好友程式集
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9912fa70014a8828e994cf528644aaa7cb351fea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159490"
---
# <a name="how-to-create-signed-friend-assemblies"></a>如何：創建簽名的好友程式集
此範例示範如何搭配具有強式名稱的組件使用 friend 組件。 這兩個組件都必須具有強式名稱。 雖然此範例中的兩個組件使用相同的金鑰，但您可以針對這兩個組件使用不同的金鑰。  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a>創建已簽名的程式集和友元程式集  
  
1. 開啟命令提示字元。  
  
2. 使用下列命令順序和強式名稱工具，產生金鑰檔並顯示其公開金鑰。 有關詳細資訊，請參閱[Sn.exe（強式名稱工具）。](../../framework/tools/sn-exe-strong-name-tool.md)  
  
    1. 為此示例生成強式名稱鍵，並將其存儲在檔*FriendAssemblies.snk*中：  
  
         `sn -k FriendAssemblies.snk`  
  
    2. 從*好友程式集中提取*公開金鑰，並將其放入 *"好友程式集"中*。  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. 顯示存儲在檔*FriendAssemblies.publickey*中的公開金鑰：  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. 創建名為*friend_signed_A*的 C# 或 Visual Basic 檔，其中包含以下代碼。 代碼使用 該<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性將*friend_signed_B*聲明為友用程式集。  

   強式名稱工具會在每次執行時產生新的公開金鑰。 因此，您必須將下列程式碼中的公開金鑰取代為剛產生的公開金鑰，如下列範例所示。  

   ```csharp  
   // friend_signed_A.cs  
   // Compile with:
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  

   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  

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

4. 使用以下命令編譯和簽名*friend_signed_A。*  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. 創建名為*friend_signed_B*的 C# 或 Visual Basic 檔，其中包含以下代碼。 由於*friend_signed_A*指定*friend_signed_B*作為友用程式集，*因此friend_signed_B*中的代碼可以從`internal``Friend`*friend_signed_A*訪問 （C#） 或 （可視基本）類型和成員。 該檔案包含下列程式碼。  

   ```csharp  
   // friend_signed_B.cs  
   // Compile with:
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  

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

6. 使用以下命令編譯和簽名*friend_signed_B。*  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱。 您必須使用`-out`編譯器選項顯式指定輸出程式集 *（.exe*或 *.dll）* 的名稱。 有關詳細資訊，請參閱[-out （C# 編譯器選項）](../../csharp/language-reference/compiler-options/out-compiler-option.md)或[-out （可視基本）](../../visual-basic/reference/command-line-compiler/out.md)。  

7. 運行*friend_signed_B.exe*檔。  

   程式輸出字串**Class1.Test**。  
  
## <a name="net-security"></a>.NET 安全性  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似性。 主要<xref:System.Security.Permissions.StrongNameIdentityPermission>區別是可以請求安全許可權來運行特定代碼部分，<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>而屬性控制 （C#） 或`internal``Friend`（Visual Basic） 類型和成員的可見度。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET 中的組件](index.md)
- [好友程式集](friend.md)
- [如何：創建未簽名的好友程式集](create-unsigned-friend.md)
- [-金鑰檔 （C#）](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [-鍵檔（可視基本）](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Sn.exe（強式名稱工具）](../../framework/tools/sn-exe-strong-name-tool.md)
- [建立和使用強式名稱的組件](create-use-strong-named.md)
- [C# 程式設計指南](../../csharp/programming-guide/index.md)
- [程式設計概念（視覺基礎）](../../visual-basic/programming-guide/concepts/index.md)
