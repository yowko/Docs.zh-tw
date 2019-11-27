---
title: 如何：尋找元件的完整名稱
ms.date: 08/20/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 49ebaeabee7a346fb84f09e5a9e34590d1ea9811
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348204"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a><span data-ttu-id="a222f-102">如何：尋找元件的完整名稱</span><span class="sxs-lookup"><span data-stu-id="a222f-102">How to: Find an assembly's fully qualified name</span></span>

<span data-ttu-id="a222f-103">若要在全域組件快取中探索 .NET Framework 元件的完整名稱，請使用全域組件快取工具（[Gacutil .exe](../../framework/tools/gacutil-exe-gac-tool.md)）。</span><span class="sxs-lookup"><span data-stu-id="a222f-103">To discover the fully qualified name of a .NET Framework assembly in the global assembly cache, use the Global Assembly Cache tool ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="a222f-104">請參閱[如何：查看全域組件快取的內容](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="a222f-104">See [How to: View the contents of the global assembly cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>

<span data-ttu-id="a222f-105">針對 .NET Core 元件，以及不在全域組件快取中的 .NET Framework 元件，您可以透過數種方式取得完整的元件名稱：</span><span class="sxs-lookup"><span data-stu-id="a222f-105">For .NET Core assemblies, and for .NET Framework assemblies that aren't in the global assembly cache, you can get the fully qualified assembly name in a number of ways:</span></span>

- <span data-ttu-id="a222f-106">您可以使用程式碼，將資訊輸出到主控台或變數，或者您可以使用[Ildasm （IL](../../framework/tools/ildasm-exe-il-disassembler.md)解譯器）來檢查元件的中繼資料（其中包含完整名稱）。</span><span class="sxs-lookup"><span data-stu-id="a222f-106">You can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

- <span data-ttu-id="a222f-107">如果應用程式已經載入組件時，您可以擷取 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> 屬性的值來取得完整名稱。</span><span class="sxs-lookup"><span data-stu-id="a222f-107">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="a222f-108">您可以使用該元件中所定義之 <xref:System.Type> 的 <xref:System.Type.Assembly> 屬性，來抓取 <xref:System.Reflection.Assembly> 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="a222f-108">You can use the <xref:System.Type.Assembly> property of a <xref:System.Type> defined in that assembly to retrieve a reference to the <xref:System.Reflection.Assembly> object.</span></span> <span data-ttu-id="a222f-109">這個範例將提供說明。</span><span class="sxs-lookup"><span data-stu-id="a222f-109">The example provides an illustration.</span></span>

- <span data-ttu-id="a222f-110">如果您知道元件的檔案系統路徑，您可以呼叫 `static` （C#）或 `Shared` （Visual Basic） <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> 方法來取得完整的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="a222f-110">If you know the assembly's file system path, you can call the `static` (C#) or `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="a222f-111">以下是一個簡單的範例。</span><span class="sxs-lookup"><span data-stu-id="a222f-111">The following is a simple example.</span></span>

  ```csharp
  using System;
  using System.Reflection;

  public class Example
  {
     public static void Main()
     {
        Console.WriteLine(AssemblyName.GetAssemblyName(@".\UtilityLibrary.dll"));
     }
  }
  // The example displays output like the following:
  //   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

  ```vb
  Imports System.Reflection

  Public Module Example
     Public Sub Main
        Console.WriteLine(AssemblyName.GetAssemblyName(".\UtilityLibrary.dll"))
     End Sub
  End Module
  ' The example displays output like the following:
  '   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

- <span data-ttu-id="a222f-112">您可以使用 [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md) 來檢查組件的中繼資料，其中包含完整名稱。</span><span class="sxs-lookup"><span data-stu-id="a222f-112">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

<span data-ttu-id="a222f-113">如需設定元件屬性的詳細資訊，例如版本、文化特性和元件名稱，請參閱[設定元件屬性](set-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="a222f-113">For more information about setting assembly attributes such as version, culture, and assembly name, see [Set assembly attributes](set-attributes.md).</span></span> <span data-ttu-id="a222f-114">如需為元件提供強式名稱的詳細資訊，請參閱[建立和使用強式名稱的元件](create-use-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="a222f-114">For more information about giving an assembly a strong name, see [Create and use strong-named assemblies](create-use-strong-named.md).</span></span>

## <a name="example"></a><span data-ttu-id="a222f-115">範例</span><span class="sxs-lookup"><span data-stu-id="a222f-115">Example</span></span>

<span data-ttu-id="a222f-116">下列範例顯示如何將包含指定類別的元件完整名稱顯示至主控台。</span><span class="sxs-lookup"><span data-stu-id="a222f-116">The following example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="a222f-117">它會使用 <xref:System.Type.Assembly?displayProperty=nameWithType> 屬性，從該元件中定義的類型抓取元件的參考。</span><span class="sxs-lookup"><span data-stu-id="a222f-117">It uses the <xref:System.Type.Assembly?displayProperty=nameWithType> property to retrieve a reference to an assembly from a type that's defined in that assembly.</span></span>

```cpp
#using <System.dll>
#using <System.Data.dll>

using namespace System;
using namespace System::Reflection;

ref class asmname
{
public:
    static void Main()
    {
        Type^ t = System::Data::DataSet::typeid;
        String^ s = t->Assembly->FullName->ToString();
        Console::WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
};

int main()
{
    asmname::Main();
}
```

```csharp
using System;
using System.Reflection;

class asmname
{
    public static void Main()
    {
        Type t = typeof(System.Data.DataSet);
        string s = t.Assembly.FullName.ToString();
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
}
```

```vb
Imports System.Reflection

Class asmname
    Public Shared Sub Main()
        Dim t As Type = GetType(System.Data.DataSet)
        Dim s As String = t.Assembly.FullName.ToString()
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s)
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="a222f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a222f-118">See also</span></span>

- [<span data-ttu-id="a222f-119">元件名稱</span><span class="sxs-lookup"><span data-stu-id="a222f-119">Assembly names</span></span>](names.md)
- [<span data-ttu-id="a222f-120">建立元件</span><span class="sxs-lookup"><span data-stu-id="a222f-120">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="a222f-121">建立和使用強式名稱的元件</span><span class="sxs-lookup"><span data-stu-id="a222f-121">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="a222f-122">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="a222f-122">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="a222f-123">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="a222f-123">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
