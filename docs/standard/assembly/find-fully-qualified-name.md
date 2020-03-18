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
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a>如何：查找程式集的完全限定名稱

要在全域組件快取中發現 .NET 框架程式集的完全限定名稱，請使用全域組件快取工具[（Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)）。 [請參閱如何：查看全域組件快取的內容](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md)。

對於 .NET Core 程式集和不在全域組件快取中的 .NET 框架程式集，您可以通過多種方式獲取完全限定的程式集名稱：

- 您可以使用代碼將資訊輸出到主控台或變數，也可以使用[Ildasm.exe （IL 拆解器）](../../framework/tools/ildasm-exe-il-disassembler.md)檢查程式集的中繼資料，該中繼資料包含完全限定的名稱。

- 如果應用程式已經載入組件時，您可以擷取 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> 屬性的值來取得完整名稱。 可以使用該程式集中<xref:System.Type.Assembly><xref:System.Type>定義的屬性來檢索對<xref:System.Reflection.Assembly>物件的引用。 這個範例將提供說明。

- 如果知道程式集的檔案系統路徑，則可以調用`static`（C#） 或`Shared`（Visual Basic）<xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType>方法來獲取完全限定的程式集名稱。 以下是簡單的範例。

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

- 您可以使用 [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md) 來檢查組件的中繼資料，其中包含完整名稱。

有關設置程式集屬性（如版本、區域性和程式集名稱）的詳細資訊，請參閱[設置程式集屬性](set-attributes.md)。 有關為程式集指定強式名稱的詳細資訊，請參閱[創建和使用強命名程式集](create-use-strong-named.md)。

## <a name="example"></a>範例

下面的示例演示如何向主控台顯示包含指定類的程式集的完全限定名稱。 它使用<xref:System.Type.Assembly?displayProperty=nameWithType>屬性從該程式集中定義的類型檢索對程式集的引用。

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

## <a name="see-also"></a>另請參閱

- [組件名稱](names.md)
- [建立組件](create.md)
- [建立和使用強式名稱的組件](create-use-strong-named.md)
- [全域組件快取](../../framework/app-domains/gac.md)
- [運行時如何定位程式集](../../framework/deployment/how-the-runtime-locates-assemblies.md)
