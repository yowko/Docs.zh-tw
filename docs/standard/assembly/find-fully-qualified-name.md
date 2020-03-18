---
title: 如何：查找程式集的完全限定名稱
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348204"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a><span data-ttu-id="8b1fc-102">如何：查找程式集的完全限定名稱</span><span class="sxs-lookup"><span data-stu-id="8b1fc-102">How to: Find an assembly's fully qualified name</span></span>

<span data-ttu-id="8b1fc-103">要在全域組件快取中發現 .NET 框架程式集的完全限定名稱，請使用全域組件快取工具[（Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)）。</span><span class="sxs-lookup"><span data-stu-id="8b1fc-103">To discover the fully qualified name of a .NET Framework assembly in the global assembly cache, use the Global Assembly Cache tool ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="8b1fc-104">[請參閱如何：查看全域組件快取的內容](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="8b1fc-104">See [How to: View the contents of the global assembly cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>

<span data-ttu-id="8b1fc-105">對於 .NET Core 程式集和不在全域組件快取中的 .NET 框架程式集，您可以通過多種方式獲取完全限定的程式集名稱：</span><span class="sxs-lookup"><span data-stu-id="8b1fc-105">For .NET Core assemblies, and for .NET Framework assemblies that aren't in the global assembly cache, you can get the fully qualified assembly name in a number of ways:</span></span>

- <span data-ttu-id="8b1fc-106">您可以使用代碼將資訊輸出到主控台或變數，也可以使用[Ildasm.exe （IL 拆解器）](../../framework/tools/ildasm-exe-il-disassembler.md)檢查程式集的中繼資料，該中繼資料包含完全限定的名稱。</span><span class="sxs-lookup"><span data-stu-id="8b1fc-106">You can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

- <span data-ttu-id="8b1fc-107">如果應用程式已經載入組件時，您可以擷取 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> 屬性的值來取得完整名稱。</span><span class="sxs-lookup"><span data-stu-id="8b1fc-107">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="8b1fc-108">可以使用該程式集中<xref:System.Type.Assembly><xref:System.Type>定義的屬性來檢索對<xref:System.Reflection.Assembly>物件的引用。</span><span class="sxs-lookup"><span data-stu-id="8b1fc-108">You can use the <xref:System.Type.Assembly> property of a <xref:System.Type> defined in that assembly to retrieve a reference to the <xref:System.Reflection.Assembly> object.</span></span> <span data-ttu-id="8b1fc-109">這個範例將提供說明。</span><span class="sxs-lookup"><span data-stu-id="8b1fc-109">The example provides an illustration.</span></span>

- <span data-ttu-id="8b1fc-110">如果知道程式集的檔案系統路徑，則可以調用`static`（C#） 或`Shared`（Visual Basic）<xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType>方法來獲取完全限定的程式集名稱。</span><span class="sxs-lookup"><span data-stu-id="8b1fc-110">If you know the assembly's file system path, you can call the `static` (C#) or `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="8b1fc-111">以下是簡單的範例。</span><span class="sxs-lookup"><span data-stu-id="8b1fc-111">The following is a simple example.</span></span>

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

- <span data-ttu-id="8b1fc-112">您可以使用 [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md) 來檢查組件的中繼資料，其中包含完整名稱。</span><span class="sxs-lookup"><span data-stu-id="8b1fc-112">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

<span data-ttu-id="8b1fc-113">有關設置程式集屬性（如版本、區域性和程式集名稱）的詳細資訊，請參閱[設置程式集屬性](set-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="8b1fc-113">For more information about setting assembly attributes such as version, culture, and assembly name, see [Set assembly attributes](set-attributes.md).</span></span> <span data-ttu-id="8b1fc-114">有關為程式集指定強式名稱的詳細資訊，請參閱[創建和使用強命名程式集](create-use-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="8b1fc-114">For more information about giving an assembly a strong name, see [Create and use strong-named assemblies](create-use-strong-named.md).</span></span>

## <a name="example"></a><span data-ttu-id="8b1fc-115">範例</span><span class="sxs-lookup"><span data-stu-id="8b1fc-115">Example</span></span>

<span data-ttu-id="8b1fc-116">下面的示例演示如何向主控台顯示包含指定類的程式集的完全限定名稱。</span><span class="sxs-lookup"><span data-stu-id="8b1fc-116">The following example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="8b1fc-117">它使用<xref:System.Type.Assembly?displayProperty=nameWithType>屬性從該程式集中定義的類型檢索對程式集的引用。</span><span class="sxs-lookup"><span data-stu-id="8b1fc-117">It uses the <xref:System.Type.Assembly?displayProperty=nameWithType> property to retrieve a reference to an assembly from a type that's defined in that assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8b1fc-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b1fc-118">See also</span></span>

- [<span data-ttu-id="8b1fc-119">組件名稱</span><span class="sxs-lookup"><span data-stu-id="8b1fc-119">Assembly names</span></span>](names.md)
- [<span data-ttu-id="8b1fc-120">建立組件</span><span class="sxs-lookup"><span data-stu-id="8b1fc-120">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="8b1fc-121">建立和使用強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="8b1fc-121">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="8b1fc-122">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="8b1fc-122">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="8b1fc-123">運行時如何定位程式集</span><span class="sxs-lookup"><span data-stu-id="8b1fc-123">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
