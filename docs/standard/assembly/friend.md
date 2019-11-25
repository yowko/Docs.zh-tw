---
title: Friend 組件
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: a74d4b74ead8492028a092e090f9281231802a87
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348170"
---
# <a name="friend-assemblies"></a><span data-ttu-id="3ecad-102">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="3ecad-102">Friend assemblies</span></span>

<span data-ttu-id="3ecad-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span><span class="sxs-lookup"><span data-stu-id="3ecad-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="3ecad-104">如果將組件指定為 friend 組件，就不再需要將類型和成員標記為 public，以供其他組件存取。</span><span class="sxs-lookup"><span data-stu-id="3ecad-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="3ecad-105">這在下列情況下特別方便：</span><span class="sxs-lookup"><span data-stu-id="3ecad-105">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="3ecad-106">在單元測試期間，當測試程式碼在另一個組件中執行，但需要存取所測試組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。</span><span class="sxs-lookup"><span data-stu-id="3ecad-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="3ecad-107">當您要開發類別庫且類別庫的新增項目包含在不同的組件，但需要存取現有組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。</span><span class="sxs-lookup"><span data-stu-id="3ecad-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ecad-108">備註</span><span class="sxs-lookup"><span data-stu-id="3ecad-108">Remarks</span></span>

<span data-ttu-id="3ecad-109">您可以使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性找出指定組件的一或多個 Friend 組件。</span><span class="sxs-lookup"><span data-stu-id="3ecad-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="3ecad-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span><span class="sxs-lookup"><span data-stu-id="3ecad-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="3ecad-111">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3ecad-111">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="3ecad-112">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file ( *.exe* or *.dll*) by using the **-out** compiler option.</span><span class="sxs-lookup"><span data-stu-id="3ecad-112">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **-out** compiler option.</span></span> <span data-ttu-id="3ecad-113">因為編譯器尚未針對在繫結至外部參考時所建立的組件產生名稱，所以這是必要動作。</span><span class="sxs-lookup"><span data-stu-id="3ecad-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="3ecad-114">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="3ecad-114">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

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

```vb
Imports System.Runtime.CompilerServices
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

<span data-ttu-id="3ecad-115">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span><span class="sxs-lookup"><span data-stu-id="3ecad-115">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="3ecad-116">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span><span class="sxs-lookup"><span data-stu-id="3ecad-116">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="3ecad-117">編譯器會執行一些被傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱的基本驗證。</span><span class="sxs-lookup"><span data-stu-id="3ecad-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="3ecad-118">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span><span class="sxs-lookup"><span data-stu-id="3ecad-118">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="3ecad-119">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span><span class="sxs-lookup"><span data-stu-id="3ecad-119">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="3ecad-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="3ecad-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="3ecad-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="3ecad-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="3ecad-122">Don't include the assembly version, culture, architecture, or public key token.</span><span class="sxs-lookup"><span data-stu-id="3ecad-122">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="3ecad-123">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span><span class="sxs-lookup"><span data-stu-id="3ecad-123">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="3ecad-124">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span><span class="sxs-lookup"><span data-stu-id="3ecad-124">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="3ecad-125">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span><span class="sxs-lookup"><span data-stu-id="3ecad-125">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="3ecad-126">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span><span class="sxs-lookup"><span data-stu-id="3ecad-126">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="3ecad-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> 類別也會提供共用類型的功能，但有下列差異：</span><span class="sxs-lookup"><span data-stu-id="3ecad-127">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="3ecad-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> 適用於個別類型，而 Friend 組件適用於整個組件。</span><span class="sxs-lookup"><span data-stu-id="3ecad-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="3ecad-129">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span><span class="sxs-lookup"><span data-stu-id="3ecad-129">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="3ecad-130">如果使用 friend 組件，您只需要宣告 friend 關聯性一次。</span><span class="sxs-lookup"><span data-stu-id="3ecad-130">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="3ecad-131">如果您使用 <xref:System.Security.Permissions.StrongNameIdentityPermission>，則您想要共用的類型必須宣告為公用。</span><span class="sxs-lookup"><span data-stu-id="3ecad-131">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="3ecad-132">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3ecad-132">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="3ecad-133">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="3ecad-133">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3ecad-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="3ecad-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="3ecad-135">How to: Create unsigned friend assemblies</span><span class="sxs-lookup"><span data-stu-id="3ecad-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="3ecad-136">How to: Create signed friend assemblies</span><span class="sxs-lookup"><span data-stu-id="3ecad-136">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="3ecad-137">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="3ecad-137">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="3ecad-138">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3ecad-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3ecad-139">Programming concepts (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ecad-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
