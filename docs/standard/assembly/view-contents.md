---
title: 'How to: View assembly contents'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 72b02209d74b6b183af6c11d9bd037889ea08543
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347048"
---
# <a name="how-to-view-assembly-contents"></a>How to: View assembly contents

您可以使用 [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md) 來檢視檔案中的 Microsoft 中繼語言 (MSIL) 資訊。 If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies. This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.

To display the contents of an assembly using *Ildasm.exe*, enter **ildasm \<assembly name>** at a command prompt. For example, the following command disassembles the *Hello.exe* assembly.

```cmd
ildasm Hello.exe
```

To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.

## <a name="example"></a>範例

The following example starts with a basic "Hello World" program. After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:

```output
// Metadata version: v4.0.30319
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 4:0:0:0
}
.assembly Hello
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module Hello.exe
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x00600000
```

The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:

|指示詞|描述|
|---------------|-----------------|
|**.assembly extern \<assembly name>**|指定另一個組件，其中包含目前模組所參考的項目 (在此範例中為 `mscorlib`)。|
|**.publickeytoken \<token>**|指定所參考組件之實際金鑰的權杖。|
|**.ver \<version number>**|指定所參考組件的版本號碼。|
|**.assembly \<assembly name>**|指定組件名稱。|
|**.hash algorithm \<int32 value>**|指定使用的雜湊演算法。|
|**.ver \<version number>**|指定組件的版本號碼。|
|**.module \<file name>**|指定構成組件之模組的名稱。 在此範例中，組件只包含一個檔案。|
|**.subsystem \<value>**|指定程式所需的應用程式環境。 在此範例中，值 3 指出從主控台執行這個可執行檔。|
|**.corflags**|中繼資料中目前保留的欄位。|

根據組件的內容，組件資訊清單可以包含許多不同的指示詞。 For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":

- [ECMA C# and Common Language Infrastructure standards](/dotnet/standard/components#applicable-standards)
- [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a>請參閱

- [應用程式定義域和組件](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [Application domains and assemblies how-to topics](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md)
