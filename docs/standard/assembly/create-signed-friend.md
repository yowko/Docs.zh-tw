---
title: 如何：建立已簽署的 friend 元件
description: 本文說明如何使用 friend 元件搭配具有強式名稱的元件。 其中包含 .NET 安全性的相關資訊。
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: b6176afed44e32911a37a0d753cea2bae7d8554e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378547"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="4c65b-104">如何：建立已簽署的 friend 元件</span><span class="sxs-lookup"><span data-stu-id="4c65b-104">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="4c65b-105">此範例示範如何搭配具有強式名稱的組件使用 friend 組件。</span><span class="sxs-lookup"><span data-stu-id="4c65b-105">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="4c65b-106">這兩個組件都必須具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="4c65b-106">Both assemblies must be strong named.</span></span> <span data-ttu-id="4c65b-107">雖然此範例中的兩個組件使用相同的金鑰，但您可以針對這兩個組件使用不同的金鑰。</span><span class="sxs-lookup"><span data-stu-id="4c65b-107">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="4c65b-108">建立已簽署的元件和 friend 元件</span><span class="sxs-lookup"><span data-stu-id="4c65b-108">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="4c65b-109">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="4c65b-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="4c65b-110">使用下列命令順序和強式名稱工具，產生金鑰檔並顯示其公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="4c65b-110">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="4c65b-111">如需詳細資訊，請參閱[sn.exe （強式名稱工具）](../../framework/tools/sn-exe-strong-name-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="4c65b-111">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="4c65b-112">產生此範例的強式名稱金鑰，並將它儲存在*FriendAssemblies*檔案中：</span><span class="sxs-lookup"><span data-stu-id="4c65b-112">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="4c65b-113">從*FriendAssemblies*解壓縮公開金鑰，並將它放入*FriendAssemblies. publickey*：</span><span class="sxs-lookup"><span data-stu-id="4c65b-113">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="4c65b-114">顯示儲存在檔案*FriendAssemblies. publickey*中的公開金鑰：</span><span class="sxs-lookup"><span data-stu-id="4c65b-114">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="4c65b-115">建立名為*friend_signed_A*的 c # 或 Visual Basic 檔案，其中包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="4c65b-115">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="4c65b-116">程式碼會使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性，將*friend_signed_B*宣告為 friend 元件。</span><span class="sxs-lookup"><span data-stu-id="4c65b-116">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  

   <span data-ttu-id="4c65b-117">強式名稱工具會在每次執行時產生新的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="4c65b-117">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="4c65b-118">因此，您必須將下列程式碼中的公開金鑰取代為剛產生的公開金鑰，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4c65b-118">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  

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

4. <span data-ttu-id="4c65b-119">使用下列命令來編譯和簽署*friend_signed_A* 。</span><span class="sxs-lookup"><span data-stu-id="4c65b-119">Compile and sign *friend_signed_A* by using the following command.</span></span>  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. <span data-ttu-id="4c65b-120">建立名為*friend_signed_B*的 c # 或 Visual Basic 檔案，其中包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="4c65b-120">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="4c65b-121">由於*friend_signed_A*會將*friend_signed_B*指定為 friend 元件，因此*friend_signed_B*中的程式碼可以 `internal` 從 friend_signed_A 存取（c #）或 `Friend` （ \* \*Visual Basic）類型和成員。</span><span class="sxs-lookup"><span data-stu-id="4c65b-121">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="4c65b-122">該檔案包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="4c65b-122">The file contains the following code.</span></span>  

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

6. <span data-ttu-id="4c65b-123">使用下列命令來編譯和簽署*friend_signed_B* 。</span><span class="sxs-lookup"><span data-stu-id="4c65b-123">Compile and sign *friend_signed_B* by using the following command.</span></span>  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   <span data-ttu-id="4c65b-124">編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱。</span><span class="sxs-lookup"><span data-stu-id="4c65b-124">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="4c65b-125">您必須使用編譯器選項，明確指定輸出元件（*.exe*或 *.dll*）的名稱 `-out` 。</span><span class="sxs-lookup"><span data-stu-id="4c65b-125">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="4c65b-126">如需詳細資訊，請參閱[-out （c # 編譯器選項）](../../csharp/language-reference/compiler-options/out-compiler-option.md)或[-out （Visual Basic）](../../visual-basic/reference/command-line-compiler/out.md)。</span><span class="sxs-lookup"><span data-stu-id="4c65b-126">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  

7. <span data-ttu-id="4c65b-127">執行*friend_signed_B .exe*檔案。</span><span class="sxs-lookup"><span data-stu-id="4c65b-127">Run the *friend_signed_B.exe* file.</span></span>  

   <span data-ttu-id="4c65b-128">程式會輸出字串**Class1。 Test**。</span><span class="sxs-lookup"><span data-stu-id="4c65b-128">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="4c65b-129">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="4c65b-129">.NET security</span></span>  
 <span data-ttu-id="4c65b-130"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似性。</span><span class="sxs-lookup"><span data-stu-id="4c65b-130">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="4c65b-131">主要差異在於， <xref:System.Security.Permissions.StrongNameIdentityPermission> 可以要求安全性許可權來執行特定的程式碼區段，而屬性則 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 控制 `internal` （c #）或 `Friend` （Visual Basic）類型和成員的可見度。</span><span class="sxs-lookup"><span data-stu-id="4c65b-131">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c65b-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="4c65b-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="4c65b-133">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="4c65b-133">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="4c65b-134">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="4c65b-134">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="4c65b-135">如何：建立未簽署的 friend 元件</span><span class="sxs-lookup"><span data-stu-id="4c65b-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="4c65b-136">-keyfile （c #）</span><span class="sxs-lookup"><span data-stu-id="4c65b-136">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="4c65b-137">-keyfile （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4c65b-137">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="4c65b-138">Sn.exe （強式名稱工具）</span><span class="sxs-lookup"><span data-stu-id="4c65b-138">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="4c65b-139">建立和使用強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="4c65b-139">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="4c65b-140">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="4c65b-140">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4c65b-141">程式設計概念（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4c65b-141">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
