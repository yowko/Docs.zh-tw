---
title: 如何：創建未簽名的好友程式集
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: f8fec064507553b8208083578165965de2303a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352441"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="ab340-102">如何：創建未簽名的好友程式集</span><span class="sxs-lookup"><span data-stu-id="ab340-102">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="ab340-103">此範例示範如何搭配未簽署的組件使用 friend 組件。</span><span class="sxs-lookup"><span data-stu-id="ab340-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="ab340-104">創建程式集和友元程式集</span><span class="sxs-lookup"><span data-stu-id="ab340-104">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="ab340-105">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ab340-105">Open a command prompt.</span></span>

2. <span data-ttu-id="ab340-106">創建名為*friend_unsigned_A*的 C# 或 Visual Basic 檔，其中包含以下代碼。</span><span class="sxs-lookup"><span data-stu-id="ab340-106">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="ab340-107">代碼使用 該<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性將*friend_unsigned_B*聲明為友用程式集。</span><span class="sxs-lookup"><span data-stu-id="ab340-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

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

3. <span data-ttu-id="ab340-108">使用以下命令編譯和簽名*friend_unsigned_A：*</span><span class="sxs-lookup"><span data-stu-id="ab340-108">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="ab340-109">創建名為*friend_unsigned_B*的 C# 或 Visual Basic 檔，其中包含以下代碼。</span><span class="sxs-lookup"><span data-stu-id="ab340-109">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="ab340-110">由於*friend_unsigned_A*指定*friend_unsigned_B*為友用程式集，*因此friend_unsigned_B*中的代碼可以訪問`internal`（C#）`Friend`或 （可視基本）類型和*成員*，friend_unsigned_A 。</span><span class="sxs-lookup"><span data-stu-id="ab340-110">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

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

5. <span data-ttu-id="ab340-111">使用以下命令編譯*friend_unsigned_B。*</span><span class="sxs-lookup"><span data-stu-id="ab340-111">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="ab340-112">編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱。</span><span class="sxs-lookup"><span data-stu-id="ab340-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="ab340-113">您必須使用`-out`編譯器選項顯式指定輸出程式集 *（.exe*或 *.dll）* 的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab340-113">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="ab340-114">有關詳細資訊，請參閱[-out （C# 編譯器選項）](../../csharp/language-reference/compiler-options/out-compiler-option.md)或[-out （可視基本）](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="ab340-114">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="ab340-115">運行*friend_unsigned_B.exe*檔。</span><span class="sxs-lookup"><span data-stu-id="ab340-115">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="ab340-116">程式輸出兩個字串：**類 1.Test**和**類 2.Test**。</span><span class="sxs-lookup"><span data-stu-id="ab340-116">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="ab340-117">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="ab340-117">.NET security</span></span>

<span data-ttu-id="ab340-118"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似性。</span><span class="sxs-lookup"><span data-stu-id="ab340-118">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="ab340-119">主要<xref:System.Security.Permissions.StrongNameIdentityPermission>區別是可以請求安全許可權來運行代碼的特定部分，<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>而屬性控制 或`internal``Friend`（Visual Basic） 類型和成員的可見度。</span><span class="sxs-lookup"><span data-stu-id="ab340-119">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab340-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab340-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="ab340-121">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="ab340-121">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="ab340-122">好友程式集</span><span class="sxs-lookup"><span data-stu-id="ab340-122">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="ab340-123">如何：創建簽名的好友程式集</span><span class="sxs-lookup"><span data-stu-id="ab340-123">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="ab340-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ab340-124">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ab340-125">程式設計概念（視覺基礎）</span><span class="sxs-lookup"><span data-stu-id="ab340-125">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
