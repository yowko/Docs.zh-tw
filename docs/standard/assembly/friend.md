---
title: Friend 組件
description: 'Friend 元件是一種 .NET 元件，可以存取另一個元件的內部（c #）或 Friend （Visual Basic）類型和成員。'
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: 105621da2bd418c6294fa2bbec474809599cb6a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378926"
---
# <a name="friend-assemblies"></a><span data-ttu-id="dbd51-103">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="dbd51-103">Friend assemblies</span></span>

<span data-ttu-id="dbd51-104">*Friend 元件*是一種元件，可以存取另一個元件的[內部](../../csharp/language-reference/keywords/internal.md)（c #）或[friend](../../visual-basic/language-reference/modifiers/friend.md) （Visual Basic）類型和成員。</span><span class="sxs-lookup"><span data-stu-id="dbd51-104">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="dbd51-105">如果將組件指定為 friend 組件，就不再需要將類型和成員標記為 public，以供其他組件存取。</span><span class="sxs-lookup"><span data-stu-id="dbd51-105">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="dbd51-106">這在下列情況下特別方便：</span><span class="sxs-lookup"><span data-stu-id="dbd51-106">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="dbd51-107">在單元測試期間，當測試程式碼在另一個組件中執行，但需要存取所測試組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。</span><span class="sxs-lookup"><span data-stu-id="dbd51-107">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="dbd51-108">當您要開發類別庫且類別庫的新增項目包含在不同的組件，但需要存取現有組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。</span><span class="sxs-lookup"><span data-stu-id="dbd51-108">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="dbd51-109">備註</span><span class="sxs-lookup"><span data-stu-id="dbd51-109">Remarks</span></span>

<span data-ttu-id="dbd51-110">您可以使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性找出指定組件的一或多個 Friend 組件。</span><span class="sxs-lookup"><span data-stu-id="dbd51-110">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="dbd51-111">下列範例會使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> *元件 A*中的屬性，並將元件*AssemblyB*指定為 friend 元件。</span><span class="sxs-lookup"><span data-stu-id="dbd51-111">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="dbd51-112">這可讓元件*AssemblyB*存取*元件 A*中標示為 `internal` c # 或 Visual Basic 中的所有類型和成員 `Friend` 。</span><span class="sxs-lookup"><span data-stu-id="dbd51-112">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="dbd51-113">當您編譯的元件（例如*AssemblyB* ）將存取另一個元件的內部類型或內部成員（例如*元件 A*）時，您必須使用 **-out**編譯器選項明確指定輸出檔（*.exe*或 *.dll*）的名稱。</span><span class="sxs-lookup"><span data-stu-id="dbd51-113">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **-out** compiler option.</span></span> <span data-ttu-id="dbd51-114">因為編譯器尚未針對在繫結至外部參考時所建立的組件產生名稱，所以這是必要動作。</span><span class="sxs-lookup"><span data-stu-id="dbd51-114">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="dbd51-115">如需詳細資訊，請參閱[-out （c #）](../../csharp/language-reference/compiler-options/out-compiler-option.md)或[-out （Visual Basic）](../../visual-basic/reference/command-line-compiler/out.md)。</span><span class="sxs-lookup"><span data-stu-id="dbd51-115">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

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

<span data-ttu-id="dbd51-116">只有明確指定為 friend 的元件可以存取 `internal` （c #）或 `Friend` （Visual Basic）類型和成員。</span><span class="sxs-lookup"><span data-stu-id="dbd51-116">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="dbd51-117">例如，如果*AssemblyB*是*元件 a*的 Friend，而*元件 c*參考*AssemblyB*，則*元件 c*無法存取 `internal` 元件 a 中的（c #）或 `Friend` （Visual Basic） *Assembly A*類型。</span><span class="sxs-lookup"><span data-stu-id="dbd51-117">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="dbd51-118">編譯器會執行一些被傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱的基本驗證。</span><span class="sxs-lookup"><span data-stu-id="dbd51-118">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="dbd51-119">如果*元件 A*宣告*AssemblyB*為 friend 元件，則驗證規則如下所示：</span><span class="sxs-lookup"><span data-stu-id="dbd51-119">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="dbd51-120">如果*元件 A*是強式名稱，則*AssemblyB*也必須是強式名稱。</span><span class="sxs-lookup"><span data-stu-id="dbd51-120">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="dbd51-121">傳遞至屬性的 friend 元件名稱必須包含用來簽署*AssemblyB*之強式名稱金鑰的元件名稱和公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="dbd51-121">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="dbd51-122">傳遞至屬性的 friend 元件名稱 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 不可以是*AssemblyB*的強式名稱。</span><span class="sxs-lookup"><span data-stu-id="dbd51-122">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="dbd51-123">請勿包含元件版本、文化特性、架構或公開金鑰 token。</span><span class="sxs-lookup"><span data-stu-id="dbd51-123">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="dbd51-124">如果*元件 A*不是強式名稱，friend 元件名稱應該只包含元件名稱。</span><span class="sxs-lookup"><span data-stu-id="dbd51-124">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="dbd51-125">如需詳細資訊，請參閱[如何：建立未簽署的 friend 元件](create-unsigned-friend.md)。</span><span class="sxs-lookup"><span data-stu-id="dbd51-125">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="dbd51-126">如果*AssemblyB*是強式名稱，您必須使用專案設定或命令列編譯器選項，為*AssemblyB*指定強式名稱索引鍵 `/keyfile` 。</span><span class="sxs-lookup"><span data-stu-id="dbd51-126">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="dbd51-127">如需詳細資訊，請參閱[如何：建立已簽署的 friend 元件](create-signed-friend.md)。</span><span class="sxs-lookup"><span data-stu-id="dbd51-127">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="dbd51-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> 類別也會提供共用類型的功能，但有下列差異：</span><span class="sxs-lookup"><span data-stu-id="dbd51-128">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="dbd51-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> 適用於個別類型，而 Friend 組件適用於整個組件。</span><span class="sxs-lookup"><span data-stu-id="dbd51-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="dbd51-130">如果您想要與*AssemblyB*共用的*元件 A*中有數百個類型，您必須將新增 <xref:System.Security.Permissions.StrongNameIdentityPermission> 至所有專案。</span><span class="sxs-lookup"><span data-stu-id="dbd51-130">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="dbd51-131">如果使用 friend 組件，您只需要宣告 friend 關聯性一次。</span><span class="sxs-lookup"><span data-stu-id="dbd51-131">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="dbd51-132">如果您使用 <xref:System.Security.Permissions.StrongNameIdentityPermission>，則您想要共用的類型必須宣告為公用。</span><span class="sxs-lookup"><span data-stu-id="dbd51-132">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="dbd51-133">如果您使用 friend 元件，共用的類型會宣告為 `internal` （c #）或 `Friend` （Visual Basic）。</span><span class="sxs-lookup"><span data-stu-id="dbd51-133">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="dbd51-134">如需如何從模組檔案（副檔名為 .netmodule 的檔案）存取元件 `internal` （c #）或 `Friend` （Visual Basic）類型和方法的詳細 *.netmodule*資訊，請參閱[-moduleassemblyname （c #）](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)或[-moduleassemblyname （Visual Basic）](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)。</span><span class="sxs-lookup"><span data-stu-id="dbd51-134">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dbd51-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="dbd51-135">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="dbd51-136">如何：建立未簽署的 friend 元件</span><span class="sxs-lookup"><span data-stu-id="dbd51-136">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="dbd51-137">如何：建立已簽署的 friend 元件</span><span class="sxs-lookup"><span data-stu-id="dbd51-137">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="dbd51-138">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="dbd51-138">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="dbd51-139">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="dbd51-139">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="dbd51-140">程式設計概念（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="dbd51-140">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
