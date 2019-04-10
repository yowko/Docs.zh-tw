---
title: HOW TO：建立簽署的 Friend 組件 (Visual Basic)
ms.date: 03/14/2018
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
ms.openlocfilehash: 4ff32015647a565f7f68e944ae028deb7f738e28
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324665"
---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a><span data-ttu-id="6400f-102">HOW TO：建立簽署的 Friend 組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6400f-102">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="6400f-103">此範例示範如何搭配具有強式名稱的組件使用 friend 組件。</span><span class="sxs-lookup"><span data-stu-id="6400f-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="6400f-104">這兩個組件都必須具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="6400f-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="6400f-105">雖然此範例中的兩個組件使用相同的金鑰，但您可以針對這兩個組件使用不同的金鑰。</span><span class="sxs-lookup"><span data-stu-id="6400f-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="6400f-106">建立簽署的組件和 friend 組件</span><span class="sxs-lookup"><span data-stu-id="6400f-106">To create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="6400f-107">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="6400f-107">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="6400f-108">使用下列命令順序和強式名稱工具，產生金鑰檔並顯示其公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="6400f-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="6400f-109">如需詳細資訊，請參閱 < [Sn.exe （強式名稱工具）](../../../../framework/tools/sn-exe-strong-name-tool.md))。</span><span class="sxs-lookup"><span data-stu-id="6400f-109">For more information, see [Sn.exe (Strong Name Tool)](../../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
    1.  <span data-ttu-id="6400f-110">為此範例產生強式名稱金鑰，然後將它儲存在 FriendAssemblies.snk 檔案中：</span><span class="sxs-lookup"><span data-stu-id="6400f-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="6400f-111">從 FriendAssemblies.snk 擷取公開金鑰，然後將它放入 FriendAssemblies.publickey：</span><span class="sxs-lookup"><span data-stu-id="6400f-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="6400f-112">顯示儲存在 FriendAssemblies.publickey 檔案中的公開金鑰：</span><span class="sxs-lookup"><span data-stu-id="6400f-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="6400f-113">建立名為 Visual Basic 檔案`friend_signed_A`包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="6400f-113">Create a Visual Basic file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="6400f-114">程式碼會使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性宣告 friend_signed_B 為 Friend 組件。</span><span class="sxs-lookup"><span data-stu-id="6400f-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="6400f-115">強式名稱工具會在每次執行時產生新的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="6400f-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="6400f-116">因此，您必須將下列程式碼中的公開金鑰取代為剛產生的公開金鑰，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6400f-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
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
  
4. <span data-ttu-id="6400f-117">使用下列命令來編譯及簽署 friend_signed_A。</span><span class="sxs-lookup"><span data-stu-id="6400f-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```console  
    Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5. <span data-ttu-id="6400f-118">建立 Visual Basic 檔案，稱為`friend_signed_B`並包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="6400f-118">Create a Visual Basic file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="6400f-119">因為 friend_signed_A 會將 friend_signed_B 指定為 friend 組件，所以 friend_signed_B 中的程式碼可以存取 friend_signed_A 中的 `Friend` 類型和成員。</span><span class="sxs-lookup"><span data-stu-id="6400f-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `Friend` types and members from friend_signed_A.</span></span> <span data-ttu-id="6400f-120">該檔案包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="6400f-120">The file contains the following code.</span></span>  
  
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
  
6. <span data-ttu-id="6400f-121">使用下列命令來編譯及簽署 friend_signed_B。</span><span class="sxs-lookup"><span data-stu-id="6400f-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```console  
    vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     <span data-ttu-id="6400f-122">編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱。</span><span class="sxs-lookup"><span data-stu-id="6400f-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="6400f-123">您可以使用，以明確地設定組件`-out`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="6400f-123">You can explicitly set the assembly by using the `-out` compiler option.</span></span> <span data-ttu-id="6400f-124">如需詳細資訊，請參閱 < [-(Visual basic)](../../../../visual-basic/reference/command-line-compiler/out.md)。</span><span class="sxs-lookup"><span data-stu-id="6400f-124">For more information, see [-out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
7. <span data-ttu-id="6400f-125">執行 friend_signed_B.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="6400f-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="6400f-126">此程式會顯示字串"Class1.Test"。</span><span class="sxs-lookup"><span data-stu-id="6400f-126">The program displays the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6400f-127">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="6400f-127">.NET Framework Security</span></span>  
 <span data-ttu-id="6400f-128"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似性。</span><span class="sxs-lookup"><span data-stu-id="6400f-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="6400f-129">主要差異是 <xref:System.Security.Permissions.StrongNameIdentityPermission> 可以要求安全性權限執行特定的程式碼區段，而 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性則是控制 `Friend` 類型和成員的可見性。</span><span class="sxs-lookup"><span data-stu-id="6400f-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `Friend` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6400f-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6400f-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="6400f-131">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="6400f-131">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="6400f-132">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="6400f-132">Friend Assemblies</span></span>](../../../../standard/assembly/friend-assemblies.md)
- [<span data-ttu-id="6400f-133">HOW TO：建立未簽署的 Friend 組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6400f-133">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="6400f-134">-keyfile</span><span class="sxs-lookup"><span data-stu-id="6400f-134">-keyfile</span></span>](../../../../visual-basic/reference/command-line-compiler/keyfile.md)
- <span data-ttu-id="6400f-135">[Sn.exe （強式名稱工具）](../../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="6400f-135">[Sn.exe (Strong Name Tool)](../../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
- [<span data-ttu-id="6400f-136">建立和使用強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="6400f-136">Creating and Using Strong-Named Assemblies</span></span>](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="6400f-137">程式設計概念</span><span class="sxs-lookup"><span data-stu-id="6400f-137">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
