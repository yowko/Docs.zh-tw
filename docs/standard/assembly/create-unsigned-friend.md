---
title: 作法：建立未簽署的 friend 元件
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9d5699f772dba994b10408d15422faa3c5931f45
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991688"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a>作法：建立未簽署的 friend 元件

此範例示範如何搭配未簽署的組件使用 friend 組件。

## <a name="create-an-assembly-and-a-friend-assembly"></a>建立元件和 friend 元件

1. 開啟命令提示字元。

2. 建立名C#為*friend_unsigned_A*的或 Visual Basic 檔案，其中包含下列程式碼。 程式碼會使用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性，將*friend_unsigned_B*宣告為 friend 元件。

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

3. 使用下列命令來編譯和簽署*friend_unsigned_A* ：

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. 建立名C#為*friend_unsigned_B*的或 Visual Basic 檔案，其中包含下列程式碼。 由於*friend_unsigned_A*會將*friend_unsigned_B*指定為 friend 元件，因此*friend_unsigned_B*中的程式`internal`代碼C#可以從`Friend` friend_unsigned_A 存取（）或（Visual Basic）類型和成員。

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

5. 使用下列命令來編譯*friend_unsigned_B* 。

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱。 您必須使用`/out`編譯器選項，明確指定輸出元件（ *.exe*或 *.dll*）的名稱。 如需詳細資訊，請參閱[/out （C#編譯器選項）](../../csharp/language-reference/compiler-options/out-compiler-option.md)或[-out （Visual Basic）](../../visual-basic/reference/command-line-compiler/out.md)。

6. 執行*friend_unsigned_B* 。

   程式會輸出兩個字串：[ **Class1]。測試**和**Class2**。

## <a name="net-security"></a>.NET 安全性

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似性。 主要差異<xref:System.Security.Permissions.StrongNameIdentityPermission>在於可以要求安全性許可權來執行特定的程式碼區段， <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>而`internal`屬性則控制或`Friend` （Visual Basic）類型和成員的可見度。

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET 中的組件](index.md)
- [Friend 元件](friend.md)
- [如何：建立已簽署的 friend 元件](create-signed-friend.md)
- [C# 程式設計指南](../../csharp/programming-guide/index.md)
- [程式設計概念（Visual Basic）](../../visual-basic/programming-guide/concepts/index.md)
