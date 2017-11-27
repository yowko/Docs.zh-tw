---
title: "Friend 組件 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d3a37629582e4fc2606afaf606735464c0d247a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assemblies-visual-basic"></a><span data-ttu-id="1b182-102">Friend 組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b182-102">Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="1b182-103">A *friend 組件*是可以存取另一個組件的組件[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)型別和成員。</span><span class="sxs-lookup"><span data-stu-id="1b182-103">A *friend assembly* is an assembly that can access another assembly's [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) types and members.</span></span> <span data-ttu-id="1b182-104">如果將組件指定為 friend 組件，就不再需要將類型和成員標記為 public，以供其他組件存取。</span><span class="sxs-lookup"><span data-stu-id="1b182-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="1b182-105">這在下列情況下特別方便：</span><span class="sxs-lookup"><span data-stu-id="1b182-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="1b182-106">在單元測試，在執行測試程式碼時個別的組件，但是需要標示為正在測試的組件中的成員存取`Friend`。</span><span class="sxs-lookup"><span data-stu-id="1b182-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `Friend`.</span></span>  
  
-   <span data-ttu-id="1b182-107">當您正在開發的類別程式庫並新增至程式庫包含在個別組件，但需要標示為的現有組件中的成員存取`Friend`。</span><span class="sxs-lookup"><span data-stu-id="1b182-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `Friend`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b182-108">備註</span><span class="sxs-lookup"><span data-stu-id="1b182-108">Remarks</span></span>  
 <span data-ttu-id="1b182-109">您可以使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性找出指定組件的一或多個 Friend 組件。</span><span class="sxs-lookup"><span data-stu-id="1b182-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="1b182-110">下列範例會使用組件 A 中的 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性，並將組件 `AssemblyB` 指定為 Friend 組件。</span><span class="sxs-lookup"><span data-stu-id="1b182-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="1b182-111">這可讓組件 `AssemblyB` 存取組件 A 中所有標記為 `Friend` 的類型和成員。</span><span class="sxs-lookup"><span data-stu-id="1b182-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `Friend`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b182-112">如果您編譯的組件 (組件 `AssemblyB`) 會存取另一個組件 (組件 *A*) 的內部類型或內部成員，您必須使用 **/out** 編譯器選項明確指定輸出檔案的名稱 (.exe 或 .dll)。</span><span class="sxs-lookup"><span data-stu-id="1b182-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="1b182-113">因為編譯器尚未針對在繫結至外部參考時所建立的組件產生名稱，所以這是必要動作。</span><span class="sxs-lookup"><span data-stu-id="1b182-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="1b182-114">如需詳細資訊，請參閱[/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)。</span><span class="sxs-lookup"><span data-stu-id="1b182-114">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
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
  
 <span data-ttu-id="1b182-115">只有明確指定為 friend 的組件才能存取 `Friend` 類型和成員。</span><span class="sxs-lookup"><span data-stu-id="1b182-115">Only assemblies that you explicitly specify as friends can access `Friend` types and members.</span></span> <span data-ttu-id="1b182-116">例如，如果組件 B 是組件 A 的 friend，而且組件 C 參考組件 B，則 C 無法存取 A 中的 `Friend` 類型。</span><span class="sxs-lookup"><span data-stu-id="1b182-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `Friend` types in A.</span></span>  
  
 <span data-ttu-id="1b182-117">編譯器會執行一些被傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱的基本驗證。</span><span class="sxs-lookup"><span data-stu-id="1b182-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="1b182-118">如果組件 *A* 將 *B* 宣告為 friend 組件，則驗證規則如下：</span><span class="sxs-lookup"><span data-stu-id="1b182-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="1b182-119">如果組件 *A* 具有強式名稱，則組件 *B* 也必須具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="1b182-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="1b182-120">傳遞給這個屬性的 friend 組件名稱必須包含組件名稱，以及簽署組件 *B* 時所用強式名稱金鑰的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="1b182-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="1b182-121">傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱不能是組件 *B* 的強式名稱：請勿包含組件版本、文化特性、架構或公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1b182-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="1b182-122">如果組件 *A* 不具強式名稱，friend 組件名稱只應包含組件名稱。</span><span class="sxs-lookup"><span data-stu-id="1b182-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="1b182-123">如需詳細資訊，請參閱[How to： 建立未簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="1b182-123">For more information, see [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="1b182-124">如果組件 *B* 具有強式名稱，您必須使用專案設定或命令列的 `/keyfile` 編譯器選項，為組件 *B* 指定強式名稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="1b182-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="1b182-125">如需詳細資訊，請參閱[How to： 建立已簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="1b182-125">For more information, see [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="1b182-126"><xref:System.Security.Permissions.StrongNameIdentityPermission> 類別也會提供共用類型的功能，但有下列差異：</span><span class="sxs-lookup"><span data-stu-id="1b182-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="1b182-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> 適用於個別類型，而 Friend 組件適用於整個組件。</span><span class="sxs-lookup"><span data-stu-id="1b182-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="1b182-128">如果要將組件 *A* 中數百個類型與組件 *B* 共用，必須將 <xref:System.Security.Permissions.StrongNameIdentityPermission> 新增至所有類型。</span><span class="sxs-lookup"><span data-stu-id="1b182-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="1b182-129">如果使用 friend 組件，您只需要宣告 friend 關聯性一次。</span><span class="sxs-lookup"><span data-stu-id="1b182-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="1b182-130">如果您使用 <xref:System.Security.Permissions.StrongNameIdentityPermission>，則您想要共用的類型必須宣告為公用。</span><span class="sxs-lookup"><span data-stu-id="1b182-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="1b182-131">如果使用 friend 組件，共用的類型會宣告為 `Friend`。</span><span class="sxs-lookup"><span data-stu-id="1b182-131">If you use a friend assembly, the shared types are declared as `Friend`.</span></span>  
  
 <span data-ttu-id="1b182-132">如需有關如何存取組件的資訊`Friend`類型和方法，從模組檔案 （副檔名為.netmodule 檔案），請參閱[/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)。</span><span class="sxs-lookup"><span data-stu-id="1b182-132">For information about how to access an assembly's `Friend` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b182-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b182-133">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>  
 [<span data-ttu-id="1b182-134">如何： 建立未簽署的 Friend 組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b182-134">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="1b182-135">如何： 建立已簽署的 Friend 組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b182-135">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [<span data-ttu-id="1b182-136">組件和全域組件快取 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b182-136">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="1b182-137">程式設計概念</span><span class="sxs-lookup"><span data-stu-id="1b182-137">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
