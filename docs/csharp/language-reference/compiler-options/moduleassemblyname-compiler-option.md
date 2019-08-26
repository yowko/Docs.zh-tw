---
title: -moduleassemblyname (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: d57279128c0909ba3e62d55d596705cfde6be75c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606672"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="f0369-102">-moduleassemblyname (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="f0369-102">-moduleassemblyname (C# Compiler Option)</span></span>
<span data-ttu-id="f0369-103">指定 .netmodule 可以存取其非公用類型的組件。</span><span class="sxs-lookup"><span data-stu-id="f0369-103">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0369-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0369-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="f0369-105">引數</span><span class="sxs-lookup"><span data-stu-id="f0369-105">Arguments</span></span>  
 `assembly_name`  
 <span data-ttu-id="f0369-106">.netmodule 可以存取其非公用類型之組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="f0369-106">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0369-107">備註</span><span class="sxs-lookup"><span data-stu-id="f0369-107">Remarks</span></span>  
 <span data-ttu-id="f0369-108">**-moduleassemblyname** 應該在建置 .netmodule 時，以及符合下列條件時使用：</span><span class="sxs-lookup"><span data-stu-id="f0369-108">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="f0369-109">.netmodule 需要存取現有組件中的非公用類型。</span><span class="sxs-lookup"><span data-stu-id="f0369-109">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="f0369-110">您知道將在其中建置 .netmodule 之組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="f0369-110">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="f0369-111">現存組件已對將在其中建置 .netmodule 的組件授與 friend 組件的存取權。</span><span class="sxs-lookup"><span data-stu-id="f0369-111">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="f0369-112">如需建置 .netmodule 的詳細資訊，請參閱 [-target:module (C# 編譯器選項)](./target-module-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="f0369-112">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="f0369-113">如需 Friend 組件的詳細資訊，請參閱 [Friend 組件](../../../standard/assembly/friend-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="f0369-113">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="f0369-114">這個選項不適用於開發環境；只有在從命令列編譯時才可用。</span><span class="sxs-lookup"><span data-stu-id="f0369-114">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="f0369-115">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="f0369-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0369-116">範例</span><span class="sxs-lookup"><span data-stu-id="f0369-116">Example</span></span>  
 <span data-ttu-id="f0369-117">此範例會建置具有私用類型的組件，並提供 Friend 組件存取權給稱為 csman_an_assembly 的組件。</span><span class="sxs-lookup"><span data-stu-id="f0369-117">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="f0369-118">範例</span><span class="sxs-lookup"><span data-stu-id="f0369-118">Example</span></span>  
 <span data-ttu-id="f0369-119">此範例將建置的 .netmodule 會存取 moduleassemblyname_1.dll 組件中的非公用類型。</span><span class="sxs-lookup"><span data-stu-id="f0369-119">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="f0369-120">藉由得知此 .netmodule 將建置在稱為 csman_an_assembly 的組件中，因此可以指定 **-moduleassemblyname**，讓 .netmodule 將 Friend 組件存取權授與 csman_an_assembly 的組件中存取非公用類型。</span><span class="sxs-lookup"><span data-stu-id="f0369-120">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="f0369-121">範例</span><span class="sxs-lookup"><span data-stu-id="f0369-121">Example</span></span>  
 <span data-ttu-id="f0369-122">此程式碼範例將會建置 csman_an_assembly 組件，並參考之前建置的組件及 .netmodule。</span><span class="sxs-lookup"><span data-stu-id="f0369-122">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
<span data-ttu-id="f0369-123">**已呼叫 An_Internal_Class.Test**</span><span class="sxs-lookup"><span data-stu-id="f0369-123">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="f0369-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0369-124">See also</span></span>

- [<span data-ttu-id="f0369-125">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="f0369-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f0369-126">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="f0369-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
