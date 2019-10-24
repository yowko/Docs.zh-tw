---
title: 如何：建立未簽署的 friend 元件
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: d8fdc3061067d85498dc5bbed7bf324f99169a36
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774351"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="aec68-102">如何：建立未簽署的 friend 元件</span><span class="sxs-lookup"><span data-stu-id="aec68-102">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="aec68-103">此範例示範如何搭配未簽署的組件使用 friend 組件。</span><span class="sxs-lookup"><span data-stu-id="aec68-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="aec68-104">建立元件和 friend 元件</span><span class="sxs-lookup"><span data-stu-id="aec68-104">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="aec68-105">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="aec68-105">Open a command prompt.</span></span>

2. <span data-ttu-id="aec68-106">建立名C#為*friend_unsigned_A*的或 Visual Basic 檔案，其中包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="aec68-106">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="aec68-107">程式碼會使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性，將*friend_unsigned_B*宣告為 friend 元件。</span><span class="sxs-lookup"><span data-stu-id="aec68-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

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

3. <span data-ttu-id="aec68-108">使用下列命令來編譯和簽署*friend_unsigned_A* ：</span><span class="sxs-lookup"><span data-stu-id="aec68-108">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="aec68-109">建立名C#為*friend_unsigned_B*的或 Visual Basic 檔案，其中包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="aec68-109">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="aec68-110">由於*friend_unsigned_A*會將*friend_unsigned_B*指定為 Friend 元件，因此*friend_unsigned_B*中的程式碼可以C#存取來自*friend_unsigned_A*的 `internal` （）或 `Friend` （Visual Basic）類型和成員。</span><span class="sxs-lookup"><span data-stu-id="aec68-110">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

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

5. <span data-ttu-id="aec68-111">使用下列命令來編譯*friend_unsigned_B* 。</span><span class="sxs-lookup"><span data-stu-id="aec68-111">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="aec68-112">編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱。</span><span class="sxs-lookup"><span data-stu-id="aec68-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="aec68-113">您必須使用 `-out` 編譯器選項，明確指定輸出元件（ *.exe*或 *.dll*）的名稱。</span><span class="sxs-lookup"><span data-stu-id="aec68-113">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="aec68-114">如需詳細資訊，請參閱[-C# out （編譯器選項）](../../csharp/language-reference/compiler-options/out-compiler-option.md)或[-out （Visual Basic）](../../visual-basic/reference/command-line-compiler/out.md)。</span><span class="sxs-lookup"><span data-stu-id="aec68-114">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="aec68-115">執行*friend_unsigned_B* 。</span><span class="sxs-lookup"><span data-stu-id="aec68-115">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="aec68-116">程式會輸出兩個字串： **Class1. test**和**Class2**。</span><span class="sxs-lookup"><span data-stu-id="aec68-116">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="aec68-117">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="aec68-117">.NET security</span></span>

<span data-ttu-id="aec68-118"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似性。</span><span class="sxs-lookup"><span data-stu-id="aec68-118">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="aec68-119">主要差異在於 <xref:System.Security.Permissions.StrongNameIdentityPermission> 可以要求安全性許可權來執行特定的程式碼區段，而 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性則控制 `internal` 或 `Friend` （Visual Basic）類型和成員的可見度。</span><span class="sxs-lookup"><span data-stu-id="aec68-119">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="aec68-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="aec68-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="aec68-121">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="aec68-121">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="aec68-122">Friend 元件</span><span class="sxs-lookup"><span data-stu-id="aec68-122">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="aec68-123">如何：建立已簽署的 friend 元件</span><span class="sxs-lookup"><span data-stu-id="aec68-123">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="aec68-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="aec68-124">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="aec68-125">程式設計概念（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="aec68-125">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
