---
title: Friend 組件
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: a74d4b74ead8492028a092e090f9281231802a87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348170"
---
# <a name="friend-assemblies"></a><span data-ttu-id="4adbe-102">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="4adbe-102">Friend assemblies</span></span>

<span data-ttu-id="4adbe-103">*友用程式集*是可以訪問其他程式集[的內部](../../csharp/language-reference/keywords/internal.md)（C#） 或[Friend（](../../visual-basic/language-reference/modifiers/friend.md)可視基本）類型和成員的程式集。</span><span class="sxs-lookup"><span data-stu-id="4adbe-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="4adbe-104">如果將組件指定為 friend 組件，就不再需要將類型和成員標記為 public，以供其他組件存取。</span><span class="sxs-lookup"><span data-stu-id="4adbe-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="4adbe-105">這在下列情況下特別方便：</span><span class="sxs-lookup"><span data-stu-id="4adbe-105">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="4adbe-106">在單元測試期間，當測試程式碼在另一個組件中執行，但需要存取所測試組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。</span><span class="sxs-lookup"><span data-stu-id="4adbe-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="4adbe-107">當您要開發類別庫且類別庫的新增項目包含在不同的組件，但需要存取現有組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。</span><span class="sxs-lookup"><span data-stu-id="4adbe-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="4adbe-108">備註</span><span class="sxs-lookup"><span data-stu-id="4adbe-108">Remarks</span></span>

<span data-ttu-id="4adbe-109">您可以使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性找出指定組件的一或多個 Friend 組件。</span><span class="sxs-lookup"><span data-stu-id="4adbe-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="4adbe-110">下面的示例使用程式集<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>*A*中的屬性，並將*程式集 B*指定為友用程式集。</span><span class="sxs-lookup"><span data-stu-id="4adbe-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="4adbe-111">這使程式集*B*能夠訪問*程式集 A*中標記為`internal`C# 或視覺化基本版中的所有`Friend`類型和成員。</span><span class="sxs-lookup"><span data-stu-id="4adbe-111">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="4adbe-112">編譯器集（如*AssemblyB）* 以訪問程式集*A*等其他程式集的內部類型或內部成員時，必須使用 **-out**編譯器選項顯式指定輸出檔案 *（.exe*或 *.dll）* 的名稱。</span><span class="sxs-lookup"><span data-stu-id="4adbe-112">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **-out** compiler option.</span></span> <span data-ttu-id="4adbe-113">因為編譯器尚未針對在繫結至外部參考時所建立的組件產生名稱，所以這是必要動作。</span><span class="sxs-lookup"><span data-stu-id="4adbe-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="4adbe-114">有關詳細資訊，請參閱[-out （C#）](../../csharp/language-reference/compiler-options/out-compiler-option.md)或[-out （可視基本）](../../visual-basic/reference/command-line-compiler/out.md)。</span><span class="sxs-lookup"><span data-stu-id="4adbe-114">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

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

<span data-ttu-id="4adbe-115">只有您明確指定為好友的程式集才能訪問`internal`（C#）`Friend`或（可視基本）類型和成員。</span><span class="sxs-lookup"><span data-stu-id="4adbe-115">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="4adbe-116">例如，如果*程式集 B*是程式集*A*的友，*程式集 C*引用程式集*B，\*\*則程式集 C*不能訪問`Friend`*Assembly A*`internal`程式集 A 中的 （C#） 或 （可視基本）類型。</span><span class="sxs-lookup"><span data-stu-id="4adbe-116">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="4adbe-117">編譯器會執行一些被傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱的基本驗證。</span><span class="sxs-lookup"><span data-stu-id="4adbe-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="4adbe-118">如果*程式集 A*聲明*程式集 B*為友用程式集，則驗證規則如下所示：</span><span class="sxs-lookup"><span data-stu-id="4adbe-118">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="4adbe-119">如果*程式集 A*具有強式名稱，*則程式集 B*也必須強命名。</span><span class="sxs-lookup"><span data-stu-id="4adbe-119">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="4adbe-120">傳遞給屬性的友元程式集名稱必須包含程式集名稱和用於對*AssemblyB*進行簽名的強式名稱鍵的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="4adbe-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="4adbe-121">傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>該屬性的友元程式集名稱不能是*程式集 B*的強式名稱。</span><span class="sxs-lookup"><span data-stu-id="4adbe-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="4adbe-122">不包括程式集版本、區域性、體系結構或公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="4adbe-122">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="4adbe-123">如果*程式集 A*不是強式名稱，則友號程式集名稱應僅包含程式集名稱。</span><span class="sxs-lookup"><span data-stu-id="4adbe-123">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="4adbe-124">有關詳細資訊，請參閱[如何：創建未簽名的好友程式集](create-unsigned-friend.md)。</span><span class="sxs-lookup"><span data-stu-id="4adbe-124">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="4adbe-125">如果*程式集 B*是強式名稱，則必須通過使用專案設置或命令列*AssemblyB*`/keyfile`編譯器選項為程式集 B 指定強式名稱鍵。</span><span class="sxs-lookup"><span data-stu-id="4adbe-125">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="4adbe-126">有關詳細資訊，請參閱[：創建已簽名的好友程式集](create-signed-friend.md)。</span><span class="sxs-lookup"><span data-stu-id="4adbe-126">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="4adbe-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> 類別也會提供共用類型的功能，但有下列差異：</span><span class="sxs-lookup"><span data-stu-id="4adbe-127">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="4adbe-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> 適用於個別類型，而 Friend 組件適用於整個組件。</span><span class="sxs-lookup"><span data-stu-id="4adbe-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="4adbe-129">如果要與*程式集 B*共用*程式集 A*中有數百種類型，則必須將它們添加到<xref:System.Security.Permissions.StrongNameIdentityPermission>所有類型中。</span><span class="sxs-lookup"><span data-stu-id="4adbe-129">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="4adbe-130">如果使用 friend 組件，您只需要宣告 friend 關聯性一次。</span><span class="sxs-lookup"><span data-stu-id="4adbe-130">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="4adbe-131">如果您使用 <xref:System.Security.Permissions.StrongNameIdentityPermission>，則您想要共用的類型必須宣告為公用。</span><span class="sxs-lookup"><span data-stu-id="4adbe-131">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="4adbe-132">如果使用友元程式集，則共用類型將聲明為`internal`（C#） 或`Friend`（可視基本）。</span><span class="sxs-lookup"><span data-stu-id="4adbe-132">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="4adbe-133">有關如何從模組檔（具有 *.netmodule*副檔名的檔）`Friend`訪問程式集 （C#）`internal`或（可視基本）類型和方法的資訊，請參閱[-模組程式集名稱 （C#）](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)或[-模組程式集名稱 （可視基本名稱）。](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)</span><span class="sxs-lookup"><span data-stu-id="4adbe-133">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4adbe-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4adbe-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="4adbe-135">如何：創建未簽名的好友程式集</span><span class="sxs-lookup"><span data-stu-id="4adbe-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="4adbe-136">如何：創建簽名的好友程式集</span><span class="sxs-lookup"><span data-stu-id="4adbe-136">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="4adbe-137">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="4adbe-137">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="4adbe-138">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4adbe-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4adbe-139">程式設計概念（視覺基礎）</span><span class="sxs-lookup"><span data-stu-id="4adbe-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
