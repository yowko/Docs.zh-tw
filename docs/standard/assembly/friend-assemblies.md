---
title: Friend 組件 (C#)
ms.date: 03/03/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: 770eb70a5350d7d26e03cb4e605b442100da2a53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68671193"
---
# <a name="friend-assemblies"></a><span data-ttu-id="36cef-102">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="36cef-102">Friend assemblies</span></span>

<span data-ttu-id="36cef-103">「Friend 組件」  是可以存取另一個組件的 [internal](../../csharp/language-reference/keywords/internal.md) (C#，或 Visual Basic 中的 [Friend](../../visual-basic/language-reference/modifiers/friend.md)) 型別和成員組件。</span><span class="sxs-lookup"><span data-stu-id="36cef-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (in C# or [Friend](../../visual-basic/language-reference/modifiers/friend.md) in Visual Basic) types and members.</span></span> <span data-ttu-id="36cef-104">如果將組件指定為 friend 組件，就不再需要將類型和成員標記為 public，以供其他組件存取。</span><span class="sxs-lookup"><span data-stu-id="36cef-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="36cef-105">這在下列情況下特別方便：</span><span class="sxs-lookup"><span data-stu-id="36cef-105">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="36cef-106">在單元測試期間，當測試程式碼在另一個組件中執行，但需要存取所測試組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。</span><span class="sxs-lookup"><span data-stu-id="36cef-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="36cef-107">當您要開發類別庫且類別庫的新增項目包含在不同的組件，但需要存取現有組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。</span><span class="sxs-lookup"><span data-stu-id="36cef-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="36cef-108">備註</span><span class="sxs-lookup"><span data-stu-id="36cef-108">Remarks</span></span>

<span data-ttu-id="36cef-109">您可以使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性找出指定組件的一或多個 Friend 組件。</span><span class="sxs-lookup"><span data-stu-id="36cef-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="36cef-110">下列範例會使用組件 A 中的 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性，並將組件 `AssemblyB` 指定為 Friend 組件。</span><span class="sxs-lookup"><span data-stu-id="36cef-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="36cef-111">這可讓組件 `AssemblyB` 存取組件 A 中所有標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的型別和成員。</span><span class="sxs-lookup"><span data-stu-id="36cef-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="36cef-112">如果您編譯的組件 (組件 `AssemblyB`) 會存取另一個組件 (組件 *A*) 的內部類型或內部成員，您必須使用 **/out** 編譯器選項明確指定輸出檔案的名稱 (.exe 或 .dll)。</span><span class="sxs-lookup"><span data-stu-id="36cef-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="36cef-113">因為編譯器尚未針對在繫結至外部參考時所建立的組件產生名稱，所以這是必要動作。</span><span class="sxs-lookup"><span data-stu-id="36cef-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="36cef-114">如需詳細資訊，請參閱 [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) 或 [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)。</span><span class="sxs-lookup"><span data-stu-id="36cef-114">For more information, see [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="36cef-115">C#</span><span class="sxs-lookup"><span data-stu-id="36cef-115">C#</span></span>](#tab/csharp)

```csharp
using System.Runtime.CompilerServices;
using System;

[assembly: InternalsVisibleTo("AssemblyB")]

// The class is internal by default.
class FriendClass
{
    public void Test()
    {
        Console.WriteLine("Sample Class");
    }
}

// Public class that has an internal method.
public class ClassWithFriendMethod
{
    internal void Test()
    {
        Console.WriteLine("Sample Method");
    }

}
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="36cef-116">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36cef-116">Visual Basic</span></span>](#tab/vb)

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

---

<span data-ttu-id="36cef-117">只有明確指定為 Friend 的組件才能存取 `internal` (C#，或 Visual Basic 中的 `Friend`) 類型和成員。</span><span class="sxs-lookup"><span data-stu-id="36cef-117">Only assemblies that you explicitly specify as friends can access `internal` (in C# or `Friend` in Visual Basic) types and members.</span></span> <span data-ttu-id="36cef-118">例如，如果組件 B 是組件 A 的 Friend，且組件 C 參考組件 B，則 C 無法存取 A 中的 `internal` (C#，或 Visual Basic 中的 `Friend`) 型別。</span><span class="sxs-lookup"><span data-stu-id="36cef-118">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `internal` (in C# or `Friend` in Visual Basic) types in A.</span></span>

<span data-ttu-id="36cef-119">編譯器會執行一些被傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱的基本驗證。</span><span class="sxs-lookup"><span data-stu-id="36cef-119">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="36cef-120">如果組件 *A* 將 *B* 宣告為 friend 組件，則驗證規則如下：</span><span class="sxs-lookup"><span data-stu-id="36cef-120">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="36cef-121">如果組件 *A* 具有強式名稱，則組件 *B* 也必須具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="36cef-121">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="36cef-122">傳遞給這個屬性的 friend 組件名稱必須包含組件名稱，以及簽署組件 *B* 時所用強式名稱金鑰的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="36cef-122">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>

     <span data-ttu-id="36cef-123">傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱不能是組件 *B* 的強式名稱：請勿包含組件版本、文化特性、架構或公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="36cef-123">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="36cef-124">如果組件 *A* 不具強式名稱，friend 組件名稱只應包含組件名稱。</span><span class="sxs-lookup"><span data-stu-id="36cef-124">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="36cef-125">如需詳細資訊，請參閱[如何：建立未簽署的 Friend 組件 (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) 或[如何：建立未簽署的 Friend 組件 (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="36cef-125">For more information, see [How to: Create Unsigned Friend Assemblies (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) or [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>

- <span data-ttu-id="36cef-126">如果組件 *B* 具有強式名稱，您必須使用專案設定或命令列的 `/keyfile` 編譯器選項，為組件 *B* 指定強式名稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="36cef-126">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="36cef-127">如需詳細資訊，請參閱[如何：建立簽署的 Friend 組件 (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) 或[如何：建立簽署的 Friend 組件 (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="36cef-127">For more information, see [How to: Create Signed Friend Assemblies (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) or [How to: Create Signed Friend Assemblies (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>

 <span data-ttu-id="36cef-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> 類別也會提供共用類型的功能，但有下列差異：</span><span class="sxs-lookup"><span data-stu-id="36cef-128">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="36cef-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> 適用於個別類型，而 Friend 組件適用於整個組件。</span><span class="sxs-lookup"><span data-stu-id="36cef-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="36cef-130">如果要將組件 *A* 中數百個類型與組件 *B* 共用，必須將 <xref:System.Security.Permissions.StrongNameIdentityPermission> 新增至所有類型。</span><span class="sxs-lookup"><span data-stu-id="36cef-130">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="36cef-131">如果使用 friend 組件，您只需要宣告 friend 關聯性一次。</span><span class="sxs-lookup"><span data-stu-id="36cef-131">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="36cef-132">如果您使用 <xref:System.Security.Permissions.StrongNameIdentityPermission>，則您想要共用的類型必須宣告為公用。</span><span class="sxs-lookup"><span data-stu-id="36cef-132">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="36cef-133">如果使用 Friend 組件，共用型別會宣告為 `internal` (C#，或 Visual Basic 中的 `Friend`)。</span><span class="sxs-lookup"><span data-stu-id="36cef-133">If you use a friend assembly, the shared types are declared as `internal` (in C# or `Friend` in Visual Basic).</span></span>

<span data-ttu-id="36cef-134">如需如何從從模組檔 (副檔名為 .netmodule 的檔案) 存取組件的 `internal` (C#,或 Visual Basic 中的 `Friend`) 型別和方法資訊，請參閱 [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) 或 [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)。</span><span class="sxs-lookup"><span data-stu-id="36cef-134">For information about how to access an assembly's `internal` (in C# or `Friend` in Visual Basic) types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="36cef-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36cef-135">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="36cef-136">如何：建立未簽署的 Friend 組件 (C#)</span><span class="sxs-lookup"><span data-stu-id="36cef-136">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="36cef-137">如何：建立未簽署的 Friend 組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36cef-137">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="36cef-138">如何：建立簽署的 Friend 組件 (C#)</span><span class="sxs-lookup"><span data-stu-id="36cef-138">How to: Create Signed Friend Assemblies (C#)</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [<span data-ttu-id="36cef-139">如何：建立簽署的 Friend 組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36cef-139">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [<span data-ttu-id="36cef-140">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="36cef-140">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="36cef-141">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="36cef-141">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="36cef-142">程式設計概念</span><span class="sxs-lookup"><span data-stu-id="36cef-142">Programming Concepts</span></span>](../../visual-basic/programming-guide/concepts/index.md)
