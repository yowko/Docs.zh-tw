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
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 17af1140867abda960cc7543ec9ee6bc3f0b4ae9
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-create-signed-friend-assemblies-c"></a><span data-ttu-id="9ed6f-102">如何：建立簽署的 Friend 組件 (C#)</span><span class="sxs-lookup"><span data-stu-id="9ed6f-102">How to: Create Signed Friend Assemblies (C#)</span></span>
<span data-ttu-id="9ed6f-103">此範例示範如何搭配具有強式名稱的組件使用 friend 組件。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="9ed6f-104">這兩個組件都必須具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="9ed6f-105">雖然此範例中的兩個組件使用相同的金鑰，但您可以針對這兩個組件使用不同的金鑰。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="9ed6f-106">建立簽署的組件和 friend 組件</span><span class="sxs-lookup"><span data-stu-id="9ed6f-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="9ed6f-107">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="9ed6f-108">使用下列命令順序和強式名稱工具，產生金鑰檔並顯示其公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="9ed6f-109">如需詳細資訊，請參閱 [Sn.exe (強式名稱工具)](https://msdn.microsoft.com/library/k5b5tt23)。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-109">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
    1.  <span data-ttu-id="9ed6f-110">為此範例產生強式名稱金鑰，然後將它儲存在 FriendAssemblies.snk 檔案中：</span><span class="sxs-lookup"><span data-stu-id="9ed6f-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="9ed6f-111">從 FriendAssemblies.snk 擷取公開金鑰，然後將它放入 FriendAssemblies.publickey：</span><span class="sxs-lookup"><span data-stu-id="9ed6f-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="9ed6f-112">顯示儲存在 FriendAssemblies.publickey 檔案中的公開金鑰：</span><span class="sxs-lookup"><span data-stu-id="9ed6f-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="9ed6f-113">建立名為 `friend_signed_A` 並包含下列程式碼的 C# 檔案。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-113">Create a C# file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="9ed6f-114">此程式碼會使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性，將 friend_signed_B 宣告為 friend 組件。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="9ed6f-115">強式名稱工具會在每次執行時產生新的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="9ed6f-116">因此，您必須將下列程式碼中的公開金鑰取代為剛產生的公開金鑰，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
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
  
4.  <span data-ttu-id="9ed6f-117">使用下列命令來編譯及簽署 friend_signed_A。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  <span data-ttu-id="9ed6f-118">建立名為 `friend_signed_B` 並包含下列程式碼的 C# 檔案。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-118">Create a C# file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="9ed6f-119">因為 friend_signed_A 會將 friend_signed_B 指定為 friend 組件，所以 friend_signed_B 中的程式碼可以存取 friend_signed_A 中的 `internal` 類型和成員。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `internal` types and members from friend_signed_A.</span></span> <span data-ttu-id="9ed6f-120">該檔案包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-120">The file contains the following code.</span></span>  
  
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
  
6.  <span data-ttu-id="9ed6f-121">使用下列命令來編譯及簽署 friend_signed_B。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     <span data-ttu-id="9ed6f-122">編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 friend 組件名稱。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="9ed6f-123">您必須使用 `/out` 編譯器選項，明確指定輸出組件 (.exe 或 .dll) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-123">You must explicitly specify the name of the output assembly (.exe or .dll) by using the `/out` compiler option.</span></span>  <span data-ttu-id="9ed6f-124">如需詳細資訊，請參閱 [/out (C# 編譯器選項)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-124">For more information, see [/out (C# Compiler Options)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span></span>  
  
7.  <span data-ttu-id="9ed6f-125">執行 friend_signed_B.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="9ed6f-126">此程式會列印字串 "Class1.Test"。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9ed6f-127">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="9ed6f-127">.NET Framework Security</span></span>  
 <span data-ttu-id="9ed6f-128"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似處。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="9ed6f-129">主要差異在於 <xref:System.Security.Permissions.StrongNameIdentityPermission> 可以要求安全性權限來執行特定程式碼區段，而 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性則會控制 `internal` 類型和成員的可見度。</span><span class="sxs-lookup"><span data-stu-id="9ed6f-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed6f-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ed6f-130">See Also</span></span>  
 <span data-ttu-id="9ed6f-131"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="9ed6f-131"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span></span>   
<span data-ttu-id="9ed6f-132"> [組件和全域組件快取 (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="9ed6f-132"> [Assemblies and the Global Assembly Cache (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="9ed6f-133"> [Friend 組件 (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="9ed6f-133"> [Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md) </span></span>  
<span data-ttu-id="9ed6f-134"> [如何：建立未簽署的 Friend 組件 (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="9ed6f-134"> [How to: Create Unsigned Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span></span>  
<span data-ttu-id="9ed6f-135"> [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md) </span><span class="sxs-lookup"><span data-stu-id="9ed6f-135"> [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md) </span></span>  
<span data-ttu-id="9ed6f-136"> [Sn.exe (強式名稱工具)](https://msdn.microsoft.com/library/k5b5tt23) </span><span class="sxs-lookup"><span data-stu-id="9ed6f-136"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) </span></span>  
<span data-ttu-id="9ed6f-137"> [建立和使用強式名稱的組件](https://msdn.microsoft.com/library/xwb8f617) </span><span class="sxs-lookup"><span data-stu-id="9ed6f-137"> [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) </span></span>  
<span data-ttu-id="9ed6f-138"> [C# 程式設計指南](../../../../csharp/programming-guide/index.md)</span><span class="sxs-lookup"><span data-stu-id="9ed6f-138"> [C# Programming Guide](../../../../csharp/programming-guide/index.md)</span></span>
