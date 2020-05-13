---
title: 如何：建立未簽署的 friend 元件
description: 本文說明如何將 friend 元件與不帶正負號的元件搭配使用。 其中包含 .NET 安全性的相關資訊。
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: 8d3e13669c36048759fedeb3df1bfb59fd476317
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378975"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="570b6-104">如何：建立未簽署的 friend 元件</span><span class="sxs-lookup"><span data-stu-id="570b6-104">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="570b6-105">此範例示範如何搭配未簽署的組件使用 friend 組件。</span><span class="sxs-lookup"><span data-stu-id="570b6-105">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="570b6-106">建立元件和 friend 元件</span><span class="sxs-lookup"><span data-stu-id="570b6-106">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="570b6-107">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="570b6-107">Open a command prompt.</span></span>

2. <span data-ttu-id="570b6-108">建立名為*friend_unsigned_A*的 c # 或 Visual Basic 檔案，其中包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="570b6-108">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="570b6-109">程式碼會使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性，將*friend_unsigned_B*宣告為 friend 元件。</span><span class="sxs-lookup"><span data-stu-id="570b6-109">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

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

3. <span data-ttu-id="570b6-110">使用下列命令來編譯和簽署*friend_unsigned_A* ：</span><span class="sxs-lookup"><span data-stu-id="570b6-110">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="570b6-111">建立名為*friend_unsigned_B*的 c # 或 Visual Basic 檔案，其中包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="570b6-111">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="570b6-112">由於*friend_unsigned_A*會將*friend_unsigned_B*指定為 friend 元件，因此*friend_unsigned_B*中的程式碼可以 `internal` 從 friend_unsigned_A 存取（c #）或 `Friend` （ \* \*Visual Basic）類型和成員。</span><span class="sxs-lookup"><span data-stu-id="570b6-112">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

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

5. <span data-ttu-id="570b6-113">使用下列命令來編譯*friend_unsigned_B* 。</span><span class="sxs-lookup"><span data-stu-id="570b6-113">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="570b6-114">編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱。</span><span class="sxs-lookup"><span data-stu-id="570b6-114">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="570b6-115">您必須使用編譯器選項，明確指定輸出元件（*.exe*或 *.dll*）的名稱 `-out` 。</span><span class="sxs-lookup"><span data-stu-id="570b6-115">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="570b6-116">如需詳細資訊，請參閱[-out （c # 編譯器選項）](../../csharp/language-reference/compiler-options/out-compiler-option.md)或[-out （Visual Basic）](../../visual-basic/reference/command-line-compiler/out.md)。</span><span class="sxs-lookup"><span data-stu-id="570b6-116">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="570b6-117">執行*friend_unsigned_B .exe*檔案。</span><span class="sxs-lookup"><span data-stu-id="570b6-117">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="570b6-118">程式會輸出兩個字串： **Class1. test**和**Class2**。</span><span class="sxs-lookup"><span data-stu-id="570b6-118">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="570b6-119">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="570b6-119">.NET security</span></span>

<span data-ttu-id="570b6-120"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似性。</span><span class="sxs-lookup"><span data-stu-id="570b6-120">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="570b6-121">主要差異在於 <xref:System.Security.Permissions.StrongNameIdentityPermission> 可以要求安全性許可權來執行特定的程式碼區段，而 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性則控制 `internal` 或 `Friend` （Visual Basic）類型和成員的可見度。</span><span class="sxs-lookup"><span data-stu-id="570b6-121">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="570b6-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="570b6-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="570b6-123">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="570b6-123">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="570b6-124">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="570b6-124">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="570b6-125">如何：建立已簽署的 friend 元件</span><span class="sxs-lookup"><span data-stu-id="570b6-125">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="570b6-126">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="570b6-126">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="570b6-127">程式設計概念（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="570b6-127">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
