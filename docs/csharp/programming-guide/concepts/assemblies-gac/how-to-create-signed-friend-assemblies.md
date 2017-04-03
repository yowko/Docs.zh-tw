---
title: "如何：建立簽署的 Friend 組件 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 890cead4b28b8532dd7bd7f571defe7e280e4cdc
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-signed-friend-assemblies-c"></a>如何：建立簽署的 Friend 組件 (C#)
此範例示範如何搭配具有強式名稱的組件使用 friend 組件。 這兩個組件都必須具有強式名稱。 雖然此範例中的兩個組件使用相同的金鑰，但您可以針對這兩個組件使用不同的金鑰。  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>建立簽署的組件和 friend 組件  
  
1.  開啟命令提示字元。  
  
2.  使用下列命令順序和強式名稱工具，產生金鑰檔並顯示其公開金鑰。 如需詳細資訊，請參閱 [Sn.exe (強式名稱工具)](https://msdn.microsoft.com/library/k5b5tt23)。  
  
    1.  為此範例產生強式名稱金鑰，然後將它儲存在 FriendAssemblies.snk 檔案中：  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  從 FriendAssemblies.snk 擷取公開金鑰，然後將它放入 FriendAssemblies.publickey：  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  顯示儲存在 FriendAssemblies.publickey 檔案中的公開金鑰：  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  建立名為 `friend_signed_A` 並包含下列程式碼的 C# 檔案。 此程式碼會使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性，將 friend_signed_B 宣告為 friend 組件。  
  
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
  
4.  使用下列命令來編譯及簽署 friend_signed_A。  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  建立名為 `friend_signed_B` 並包含下列程式碼的 C# 檔案。 因為 friend_signed_A 會將 friend_signed_B 指定為 friend 組件，所以 friend_signed_B 中的程式碼可以存取 friend_signed_A 中的 `internal` 類型和成員。 該檔案包含下列程式碼。  
  
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
  
6.  使用下列命令來編譯及簽署 friend_signed_B。  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 friend 組件名稱。 您必須使用 `/out` 編譯器選項，明確指定輸出組件 (.exe 或 .dll) 的名稱。  如需詳細資訊，請參閱 [/out (C# 編譯器選項)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md)。  
  
7.  執行 friend_signed_B.exe 檔案。  
  
     此程式會列印字串 "Class1.Test"。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似處。 主要差異在於 <xref:System.Security.Permissions.StrongNameIdentityPermission> 可以要求安全性權限來執行特定程式碼區段，而 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性則會控制 `internal` 類型和成員的可見度。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [組件和全域組件快取 (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)   
 [Friend 組件 (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [如何：建立未簽署的 Friend 組件 (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)   
 [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [Sn.exe (強式名稱工具)](https://msdn.microsoft.com/library/k5b5tt23)   
 [建立和使用強式名稱的組件](https://msdn.microsoft.com/library/xwb8f617)   
 [C# 程式設計指南](../../../../csharp/programming-guide/index.md)
