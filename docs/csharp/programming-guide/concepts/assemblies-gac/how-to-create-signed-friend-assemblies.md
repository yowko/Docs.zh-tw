---
title: 如何：建立簽署的 Friend 組件 (C#)
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 34243a65f57f41c358439baac82a1ce169233259
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340654"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a><span data-ttu-id="e5762-102">如何：建立簽署的 Friend 組件 (C#)</span><span class="sxs-lookup"><span data-stu-id="e5762-102">How to: Create Signed Friend Assemblies (C#)</span></span>
<span data-ttu-id="e5762-103">此範例示範如何搭配具有強式名稱的組件使用 friend 組件。</span><span class="sxs-lookup"><span data-stu-id="e5762-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="e5762-104">這兩個組件都必須具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="e5762-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="e5762-105">雖然此範例中的兩個組件使用相同的金鑰，但您可以針對這兩個組件使用不同的金鑰。</span><span class="sxs-lookup"><span data-stu-id="e5762-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="e5762-106">建立簽署的組件和 friend 組件</span><span class="sxs-lookup"><span data-stu-id="e5762-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="e5762-107">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="e5762-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="e5762-108">使用下列命令順序和強式名稱工具，產生金鑰檔並顯示其公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="e5762-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="e5762-109">如需詳細資訊，請參閱 [Sn.exe (強式名稱工具)](https://msdn.microsoft.com/library/k5b5tt23)。</span><span class="sxs-lookup"><span data-stu-id="e5762-109">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
    1.  <span data-ttu-id="e5762-110">為此範例產生強式名稱金鑰，然後將它儲存在 FriendAssemblies.snk 檔案中：</span><span class="sxs-lookup"><span data-stu-id="e5762-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="e5762-111">從 FriendAssemblies.snk 擷取公開金鑰，然後將它放入 FriendAssemblies.publickey：</span><span class="sxs-lookup"><span data-stu-id="e5762-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="e5762-112">顯示儲存在 FriendAssemblies.publickey 檔案中的公開金鑰：</span><span class="sxs-lookup"><span data-stu-id="e5762-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="e5762-113">建立名為 `friend_signed_A` 並包含下列程式碼的 C# 檔案。</span><span class="sxs-lookup"><span data-stu-id="e5762-113">Create a C# file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="e5762-114">程式碼會使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性宣告 friend_signed_B 為 Friend 組件。</span><span class="sxs-lookup"><span data-stu-id="e5762-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="e5762-115">強式名稱工具會在每次執行時產生新的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="e5762-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="e5762-116">因此，您必須將下列程式碼中的公開金鑰取代為剛產生的公開金鑰，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e5762-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
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
  
4.  <span data-ttu-id="e5762-117">使用下列命令來編譯及簽署 friend_signed_A。</span><span class="sxs-lookup"><span data-stu-id="e5762-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  <span data-ttu-id="e5762-118">建立名為 `friend_signed_B` 並包含下列程式碼的 C# 檔案。</span><span class="sxs-lookup"><span data-stu-id="e5762-118">Create a C# file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="e5762-119">因為 friend_signed_A 會將 friend_signed_B 指定為 friend 組件，所以 friend_signed_B 中的程式碼可以存取 friend_signed_A 中的 `internal` 類型和成員。</span><span class="sxs-lookup"><span data-stu-id="e5762-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `internal` types and members from friend_signed_A.</span></span> <span data-ttu-id="e5762-120">該檔案包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="e5762-120">The file contains the following code.</span></span>  
  
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
  
6.  <span data-ttu-id="e5762-121">使用下列命令來編譯及簽署 friend_signed_B。</span><span class="sxs-lookup"><span data-stu-id="e5762-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     <span data-ttu-id="e5762-122">編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱。</span><span class="sxs-lookup"><span data-stu-id="e5762-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="e5762-123">您必須使用 `/out` 編譯器選項，明確指定輸出組件 (.exe 或 .dll) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="e5762-123">You must explicitly specify the name of the output assembly (.exe or .dll) by using the `/out` compiler option.</span></span>  <span data-ttu-id="e5762-124">如需詳細資訊，請參閱 [/out (C# 編譯器選項)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="e5762-124">For more information, see [/out (C# Compiler Options)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span></span>  
  
7.  <span data-ttu-id="e5762-125">執行 friend_signed_B.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="e5762-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="e5762-126">此程式會列印字串 "Class1.Test"。</span><span class="sxs-lookup"><span data-stu-id="e5762-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e5762-127">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="e5762-127">.NET Framework Security</span></span>  
 <span data-ttu-id="e5762-128"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似性。</span><span class="sxs-lookup"><span data-stu-id="e5762-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="e5762-129">主要差異是 <xref:System.Security.Permissions.StrongNameIdentityPermission> 可以要求安全性權限執行特定的程式碼區段，而 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性則是控制 `internal` 類型和成員的可見性。</span><span class="sxs-lookup"><span data-stu-id="e5762-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5762-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="e5762-130">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="e5762-131">組件和全域組件快取 (C#)</span><span class="sxs-lookup"><span data-stu-id="e5762-131">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="e5762-132">Friend 組件 (C#)</span><span class="sxs-lookup"><span data-stu-id="e5762-132">Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [<span data-ttu-id="e5762-133">如何：建立未簽署的 Friend 組件 (C#)</span><span class="sxs-lookup"><span data-stu-id="e5762-133">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="e5762-134">/keyfile</span><span class="sxs-lookup"><span data-stu-id="e5762-134">/keyfile</span></span>](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="e5762-135">Sn.exe (強式名稱工具)</span><span class="sxs-lookup"><span data-stu-id="e5762-135">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="e5762-136">建立和使用強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="e5762-136">Creating and Using Strong-Named Assemblies</span></span>](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [<span data-ttu-id="e5762-137">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e5762-137">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
