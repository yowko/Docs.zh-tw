---
title: 作法：建立未簽署的 Friend 組件 (C#)
ms.date: 07/20/2015
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
ms.openlocfilehash: 5b376266581def9bdd4315ccbee04b71b7c8bc08
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365057"
---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a>作法：建立未簽署的 Friend 組件 (C#)
此範例示範如何搭配未簽署的組件使用 friend 組件。  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>建立組件和 friend 組件  
  
1.  開啟命令提示字元。  
  
2.  建立名為 `friend_unsigned_A.` 並包含下列程式碼的 C# 檔案。 程式碼會使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性宣告 friend_unsigned_B 為 Friend 組件。  
  
    ```csharp  
    // friend_unsigned_A.cs  
    // Compile with:   
    // csc /target:library friend_unsigned_A.cs  
    using System.Runtime.CompilerServices;  
    using System;  
  
    [assembly: InternalsVisibleTo("friend_unsigned_B")]  
  
    // Type is internal by default.  
    class Class1  
    {  
        public void Test()  
        {  
            Console.WriteLine("Class1.Test");  
        }  
    }  
  
    // Public type with internal member.  
    public class Class2  
    {  
        internal void Test()  
        {  
            Console.WriteLine("Class2.Test");  
        }  
    }  
    ```  
  
3.  使用下列命令來編譯及簽署 friend_unsigned_A。  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4.  建立名為 `friend_unsigned_B` 並包含下列程式碼的 C# 檔案。 因為 friend_unsigned_A 會將 friend_unsigned_B 指定為 friend 組件，所以 friend_unsigned_B 中的程式碼可以存取 friend_unsigned_A 中的 `internal` 類型和成員。  
  
    ```csharp  
    // friend_unsigned_B.cs  
    // Compile with:   
    // csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    public class Program  
    {  
        static void Main()  
        {  
            // Access an internal type.  
            Class1 inst1 = new Class1();  
            inst1.Test();  
  
            Class2 inst2 = new Class2();  
            // Access an internal member of a public type.  
            inst2.Test();  
  
            System.Console.ReadLine();  
        }  
    }  
    ```  
  
5.  使用下列命令來編譯 friend_unsigned_B。  
  
    ```csharp  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱。 您必須使用 `/out` 編譯器選項，明確指定輸出組件 (.exe 或 .dll) 的名稱。 如需詳細資訊，請參閱 [/out (C# 編譯器選項)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md)。  
  
6.  執行 friend_unsigned_B.exe 檔案。  
  
     程式會列印兩個字串："Class1.Test" 和 "Class2.Test"。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似性。 主要差異是 <xref:System.Security.Permissions.StrongNameIdentityPermission> 可以要求安全性權限執行特定的程式碼區段，而 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性則是控制 `internal` 類型和成員的可見性。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET 中的組件](../../../../standard/assembly/index.md)
- [Friend 組件](../../../../standard/assembly/friend-assemblies.md)
- [如何：建立簽署的 Friend 組件 (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [C# 程式設計指南](../../../../csharp/programming-guide/index.md)
