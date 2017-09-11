---
title: "如何︰ 建立已簽署的 Friend 組件 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a8a7df331c8cd93de45d902cb9b6c67460952c6d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a><span data-ttu-id="dc0b6-102">如何︰ 建立已簽署的 Friend 組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc0b6-102">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="dc0b6-103">這個範例示範如何使用 friend 組件具有強式名稱的組件。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="dc0b6-104">這兩個組件必須使用強式名稱。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="dc0b6-105">雖然這兩個組件，在此範例中使用相同的金鑰，您可以使用不同的索引鍵的兩個組件。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="dc0b6-106">若要建立簽署的組件和 friend 組件</span><span class="sxs-lookup"><span data-stu-id="dc0b6-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="dc0b6-107">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="dc0b6-108">產生金鑰檔，並顯示它的公開金鑰，則您可以使用強式名稱工具以下的命令順序。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="dc0b6-109">如需詳細資訊，請參閱 [Sn.exe (強式名稱工具)](https://msdn.microsoft.com/library/k5b5tt23)。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-109">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
    1.  <span data-ttu-id="dc0b6-110">產生強式名稱金鑰，此範例中，並將它儲存在檔案 FriendAssemblies.snk:</span><span class="sxs-lookup"><span data-stu-id="dc0b6-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="dc0b6-111">從 FriendAssemblies.snk 擷取公開金鑰，並將它放入 FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="dc0b6-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="dc0b6-112">顯示儲存在檔案 FriendAssemblies.publickey 的公開金鑰︰</span><span class="sxs-lookup"><span data-stu-id="dc0b6-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="dc0b6-113">建立名為 Visual Basic 檔案`friend_signed_A`，其中包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-113">Create a Visual Basic file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="dc0b6-114">程式碼使用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性宣告為 friend 組件 friend_signed_B。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="dc0b6-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="dc0b6-115">強式名稱工具會在每次執行時產生新的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="dc0b6-116">因此，您必須取代下列程式碼中的公開金鑰您剛產生的公開金鑰，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4.  <span data-ttu-id="dc0b6-117">編譯並使用下列命令來簽署 friend_signed_A。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```vb  
    Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  <span data-ttu-id="dc0b6-118">建立名為 Visual Basic 檔案`friend_signed_B`且包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-118">Create a Visual Basic file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="dc0b6-119">由於 friend_signed_A 做為 friend 組件指定 friend_signed_B friend_signed_B 中的程式碼可以存取`Friend`型別和從 friend_signed_A 的成員。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `Friend` types and members from friend_signed_A.</span></span> <span data-ttu-id="dc0b6-120">此檔案包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-120">The file contains the following code.</span></span>  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6.  <span data-ttu-id="dc0b6-121">編譯並使用下列命令來簽署 friend_signed_B。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```vb  
    Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     <span data-ttu-id="dc0b6-122">由編譯器所產生的組件的名稱必須符合 friend 組件名稱傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="dc0b6-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="dc0b6-123">您可以使用，以明確地設定組件`/out`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-123">You can explicitly set the assembly by using the `/out` compiler option.</span></span> <span data-ttu-id="dc0b6-124">如需詳細資訊，請參閱[/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-124">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
7.  <span data-ttu-id="dc0b6-125">執行 friend_signed_B.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="dc0b6-126">程式會列印"Class1.Test"的字串。</span><span class="sxs-lookup"><span data-stu-id="dc0b6-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="dc0b6-127">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="dc0b6-127">.NET Framework Security</span></span>  
 <span data-ttu-id="dc0b6-128"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性和<xref:System.Security.Permissions.StrongNameIdentityPermission>類別</xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>之間有相似之處</span><span class="sxs-lookup"><span data-stu-id="dc0b6-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="dc0b6-129">主要差異在於<xref:System.Security.Permissions.StrongNameIdentityPermission>可以要求安全性權限才能執行特定程式碼，而<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性控制的可視性`Friend`型別和成員。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> </xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="dc0b6-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `Friend` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc0b6-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc0b6-130">See Also</span></span>  
 <span data-ttu-id="dc0b6-131"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="dc0b6-131"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span></span>   
<span data-ttu-id="dc0b6-132"> [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc0b6-132"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="dc0b6-133"> [Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="dc0b6-133"> [Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md) </span></span>  
<span data-ttu-id="dc0b6-134"> [如何︰ 建立未簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="dc0b6-134"> [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span></span>  
<span data-ttu-id="dc0b6-135"> [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md) </span><span class="sxs-lookup"><span data-stu-id="dc0b6-135"> [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md) </span></span>  
<span data-ttu-id="dc0b6-136"> [Sn.exe （強式名稱工具）](https://msdn.microsoft.com/library/k5b5tt23) </span><span class="sxs-lookup"><span data-stu-id="dc0b6-136"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) </span></span>  
<span data-ttu-id="dc0b6-137"> [建立和使用強式名稱組件](https://msdn.microsoft.com/library/xwb8f617) </span><span class="sxs-lookup"><span data-stu-id="dc0b6-137"> [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) </span></span>  
<span data-ttu-id="dc0b6-138"> [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)</span><span class="sxs-lookup"><span data-stu-id="dc0b6-138"> [Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md)</span></span>
