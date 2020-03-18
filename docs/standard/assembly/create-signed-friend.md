---
title: 如何：創建簽名的好友程式集
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9912fa70014a8828e994cf528644aaa7cb351fea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159490"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="f8a73-102">如何：創建簽名的好友程式集</span><span class="sxs-lookup"><span data-stu-id="f8a73-102">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="f8a73-103">此範例示範如何搭配具有強式名稱的組件使用 friend 組件。</span><span class="sxs-lookup"><span data-stu-id="f8a73-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="f8a73-104">這兩個組件都必須具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="f8a73-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="f8a73-105">雖然此範例中的兩個組件使用相同的金鑰，但您可以針對這兩個組件使用不同的金鑰。</span><span class="sxs-lookup"><span data-stu-id="f8a73-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="f8a73-106">創建已簽名的程式集和友元程式集</span><span class="sxs-lookup"><span data-stu-id="f8a73-106">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="f8a73-107">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f8a73-107">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="f8a73-108">使用下列命令順序和強式名稱工具，產生金鑰檔並顯示其公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="f8a73-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="f8a73-109">有關詳細資訊，請參閱[Sn.exe（強式名稱工具）。](../../framework/tools/sn-exe-strong-name-tool.md)</span><span class="sxs-lookup"><span data-stu-id="f8a73-109">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="f8a73-110">為此示例生成強式名稱鍵，並將其存儲在檔*FriendAssemblies.snk*中：</span><span class="sxs-lookup"><span data-stu-id="f8a73-110">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="f8a73-111">從*好友程式集中提取*公開金鑰，並將其放入 *"好友程式集"中*。</span><span class="sxs-lookup"><span data-stu-id="f8a73-111">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="f8a73-112">顯示存儲在檔*FriendAssemblies.publickey*中的公開金鑰：</span><span class="sxs-lookup"><span data-stu-id="f8a73-112">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="f8a73-113">創建名為*friend_signed_A*的 C# 或 Visual Basic 檔，其中包含以下代碼。</span><span class="sxs-lookup"><span data-stu-id="f8a73-113">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="f8a73-114">代碼使用 該<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性將*friend_signed_B*聲明為友用程式集。</span><span class="sxs-lookup"><span data-stu-id="f8a73-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  

   <span data-ttu-id="f8a73-115">強式名稱工具會在每次執行時產生新的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="f8a73-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="f8a73-116">因此，您必須將下列程式碼中的公開金鑰取代為剛產生的公開金鑰，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f8a73-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  

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

4. <span data-ttu-id="f8a73-117">使用以下命令編譯和簽名*friend_signed_A。*</span><span class="sxs-lookup"><span data-stu-id="f8a73-117">Compile and sign *friend_signed_A* by using the following command.</span></span>  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. <span data-ttu-id="f8a73-118">創建名為*friend_signed_B*的 C# 或 Visual Basic 檔，其中包含以下代碼。</span><span class="sxs-lookup"><span data-stu-id="f8a73-118">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="f8a73-119">由於*friend_signed_A*指定*friend_signed_B*作為友用程式集，*因此friend_signed_B*中的代碼可以從`internal``Friend`*friend_signed_A*訪問 （C#） 或 （可視基本）類型和成員。</span><span class="sxs-lookup"><span data-stu-id="f8a73-119">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="f8a73-120">該檔案包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="f8a73-120">The file contains the following code.</span></span>  

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

6. <span data-ttu-id="f8a73-121">使用以下命令編譯和簽名*friend_signed_B。*</span><span class="sxs-lookup"><span data-stu-id="f8a73-121">Compile and sign *friend_signed_B* by using the following command.</span></span>  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   <span data-ttu-id="f8a73-122">編譯器所產生之組件的名稱必須符合傳遞至 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱。</span><span class="sxs-lookup"><span data-stu-id="f8a73-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="f8a73-123">您必須使用`-out`編譯器選項顯式指定輸出程式集 *（.exe*或 *.dll）* 的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8a73-123">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="f8a73-124">有關詳細資訊，請參閱[-out （C# 編譯器選項）](../../csharp/language-reference/compiler-options/out-compiler-option.md)或[-out （可視基本）](../../visual-basic/reference/command-line-compiler/out.md)。</span><span class="sxs-lookup"><span data-stu-id="f8a73-124">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  

7. <span data-ttu-id="f8a73-125">運行*friend_signed_B.exe*檔。</span><span class="sxs-lookup"><span data-stu-id="f8a73-125">Run the *friend_signed_B.exe* file.</span></span>  

   <span data-ttu-id="f8a73-126">程式輸出字串**Class1.Test**。</span><span class="sxs-lookup"><span data-stu-id="f8a73-126">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="f8a73-127">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="f8a73-127">.NET security</span></span>  
 <span data-ttu-id="f8a73-128"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別之間有相似性。</span><span class="sxs-lookup"><span data-stu-id="f8a73-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="f8a73-129">主要<xref:System.Security.Permissions.StrongNameIdentityPermission>區別是可以請求安全許可權來運行特定代碼部分，<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>而屬性控制 （C#） 或`internal``Friend`（Visual Basic） 類型和成員的可見度。</span><span class="sxs-lookup"><span data-stu-id="f8a73-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8a73-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8a73-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="f8a73-131">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="f8a73-131">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="f8a73-132">好友程式集</span><span class="sxs-lookup"><span data-stu-id="f8a73-132">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="f8a73-133">如何：創建未簽名的好友程式集</span><span class="sxs-lookup"><span data-stu-id="f8a73-133">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="f8a73-134">-金鑰檔 （C#）</span><span class="sxs-lookup"><span data-stu-id="f8a73-134">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="f8a73-135">-鍵檔（可視基本）</span><span class="sxs-lookup"><span data-stu-id="f8a73-135">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="f8a73-136">Sn.exe（強式名稱工具）</span><span class="sxs-lookup"><span data-stu-id="f8a73-136">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="f8a73-137">建立和使用強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="f8a73-137">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="f8a73-138">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f8a73-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f8a73-139">程式設計概念（視覺基礎）</span><span class="sxs-lookup"><span data-stu-id="f8a73-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
