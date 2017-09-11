---
title: "Friend 組件 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 23c9167bf6a632b53202bdc56aebb2248065e967
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="friend-assemblies-visual-basic"></a><span data-ttu-id="49f9f-102">Friend 組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49f9f-102">Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="49f9f-103">A *friend 組件*是可以存取另一個組件的組件[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)型別和成員。</span><span class="sxs-lookup"><span data-stu-id="49f9f-103">A *friend assembly* is an assembly that can access another assembly's [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) types and members.</span></span> <span data-ttu-id="49f9f-104">如果您找出組件做為 friend 組件，您不再需要標記型別和成員為公用，才會由其他組件存取。</span><span class="sxs-lookup"><span data-stu-id="49f9f-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="49f9f-105">這是非常方便您在下列情況︰</span><span class="sxs-lookup"><span data-stu-id="49f9f-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="49f9f-106">在單元測試，測試程式碼中執行時不同的組件，但是需要標示為正在測試的組件中的成員存取`Friend`。</span><span class="sxs-lookup"><span data-stu-id="49f9f-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `Friend`.</span></span>  
  
-   <span data-ttu-id="49f9f-107">當您正在開發的類別程式庫和程式庫的新增項目都包含在不同的組件，但需要標示為的現有組件中的成員存取`Friend`。</span><span class="sxs-lookup"><span data-stu-id="49f9f-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `Friend`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49f9f-108">備註</span><span class="sxs-lookup"><span data-stu-id="49f9f-108">Remarks</span></span>  
 <span data-ttu-id="49f9f-109">您可以使用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性來識別指定的組件的一或多個 friend 組件。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="49f9f-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="49f9f-110">下列範例會使用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性在組件 A 中，指定組件`AssemblyB`做為 friend 組件。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="49f9f-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="49f9f-111">這可讓組件`AssemblyB`所有型別和組件中，標示為成員存取`Friend`。</span><span class="sxs-lookup"><span data-stu-id="49f9f-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `Friend`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49f9f-112">當您編譯組件 (組件`AssemblyB`)，將存取內部型別或內部成員的另一個組件 (組件*A*)，您必須使用明確指定輸出檔 （.exe 或.dll） 的名稱**/輸出**編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="49f9f-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="49f9f-113">這是必要的因為編譯器但尚未產生它所繫結至外部參考時，它本身正在建置的組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="49f9f-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="49f9f-114">如需詳細資訊，請參閱[/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)。</span><span class="sxs-lookup"><span data-stu-id="49f9f-114">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports System  
<Assembly: InternalsVisibleTo("AssemblyB")>   
  
' Friend class.  
Friend Class FriendClass  
    Public Sub Test()  
        Console.WriteLine("Sample Class")  
    End Sub  
End Class  
  
' Public class with a Friend method.  
Public Class ClassWithFriendMethod  
    Friend Sub Test()  
        Console.WriteLine("Sample Method")  
    End Sub  
End Class  
  
```  
  
 <span data-ttu-id="49f9f-115">只有明確指定的朋友可以存取的組件`Friend`型別和成員。</span><span class="sxs-lookup"><span data-stu-id="49f9f-115">Only assemblies that you explicitly specify as friends can access `Friend` types and members.</span></span> <span data-ttu-id="49f9f-116">例如，如果組件 A 和組件 C 參考組件 B 的 friend 組件 B，C 並沒有存取權`Friend`a 中的型別</span><span class="sxs-lookup"><span data-stu-id="49f9f-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `Friend` types in A.</span></span>  
  
 <span data-ttu-id="49f9f-117">編譯器會執行一些基本驗證的 friend 組件名稱傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="49f9f-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="49f9f-118">如果組件*A*宣告*B*做為 friend 組件中，驗證規則如下︰</span><span class="sxs-lookup"><span data-stu-id="49f9f-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="49f9f-119">如果組件*A*具有強式名稱，組件*B*也必須強式名稱。</span><span class="sxs-lookup"><span data-stu-id="49f9f-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="49f9f-120">Friend 組件名稱傳遞給該屬性必須包含組件名稱以及用來簽署組件的強式名稱金鑰的公開金鑰*B*。</span><span class="sxs-lookup"><span data-stu-id="49f9f-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="49f9f-121">Friend 組件名稱傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性不能為組件的強式名稱*B*︰ 不包含組件版本、 文化特性、 架構或公開金鑰語彙基元。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="49f9f-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="49f9f-122">如果組件*A*不是強式命名組件名稱應該包含 friend 組件名稱。</span><span class="sxs-lookup"><span data-stu-id="49f9f-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="49f9f-123">如需詳細資訊，請參閱[How to︰ 建立未簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="49f9f-123">For more information, see [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="49f9f-124">如果組件*B*具有強式名稱，您必須指定組件的強式名稱金鑰*B*的專案設定，或是在命令列使用`/keyfile`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="49f9f-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="49f9f-125">如需詳細資訊，請參閱[How to︰ 建立簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="49f9f-125">For more information, see [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="49f9f-126"><xref:System.Security.Permissions.StrongNameIdentityPermission>類別也提供共用型別，但有下列差異︰</xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="49f9f-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="49f9f-127"><xref:System.Security.Permissions.StrongNameIdentityPermission>雖然 friend 組件適用於整個組件適用於個別的型別。</xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="49f9f-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="49f9f-128">如果有數百個組件中的型別*A*您想要分享的組件*B*，您必須加入<xref:System.Security.Permissions.StrongNameIdentityPermission>至所有端點。</xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="49f9f-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="49f9f-129">如果您使用 friend 組件，您只需要一次宣告的 friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="49f9f-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="49f9f-130">如果您使用<xref:System.Security.Permissions.StrongNameIdentityPermission>，您想要共用的類型必須宣告為公用。</xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="49f9f-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="49f9f-131">如果您使用 friend 組件時，共用的類型會宣告為`Friend`。</span><span class="sxs-lookup"><span data-stu-id="49f9f-131">If you use a friend assembly, the shared types are declared as `Friend`.</span></span>  
  
 <span data-ttu-id="49f9f-132">如需有關如何存取組件的資訊`Friend`型別和方法，從模組檔案 （副檔名為.netmodule 檔案），請參閱[/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)。</span><span class="sxs-lookup"><span data-stu-id="49f9f-132">For information about how to access an assembly's `Friend` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49f9f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49f9f-133">See Also</span></span>  
 <span data-ttu-id="49f9f-134"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="49f9f-134"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span></span>   
 <span data-ttu-id="49f9f-135"><xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="49f9f-135"><xref:System.Security.Permissions.StrongNameIdentityPermission></span></span>   
<span data-ttu-id="49f9f-136"> [如何︰ 建立未簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="49f9f-136"> [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span></span>  
<span data-ttu-id="49f9f-137"> [如何︰ 建立已簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="49f9f-137"> [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span></span>  
<span data-ttu-id="49f9f-138"> [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="49f9f-138"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="49f9f-139"> [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)</span><span class="sxs-lookup"><span data-stu-id="49f9f-139"> [Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md)</span></span>
