---
title: 如何：查看程式集內容
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
ms.openlocfilehash: 179b240bb06a319ff71009e14323d5c8f2740e5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187393"
---
# <a name="how-to-view-assembly-contents"></a>如何：查看程式集內容

您可以使用 [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md) 來檢視檔案中的 Microsoft 中繼語言 (MSIL) 資訊。 如果正在檢查的檔是程式集，則此資訊可以包括程式集的屬性和對其他模組和程式集的引用。 此資訊有助於確定檔是程式集還是程式集的一部分，以及該檔是否具有對其他模組或程式集的引用。

要使用*Ildasm.exe*顯示程式集的內容，請在命令提示符下**輸入\<>的 ildasm 程式集名稱**。 例如，以下命令將拆解*Hello.exe*程式集。

```cmd
ildasm Hello.exe
```

要查看組件資訊清單資訊，請按兩下 MSIL 拆解器視窗中的 **"清單"** 圖示。

## <a name="example"></a>範例

下面的示例以基本的"你好世界"計畫開頭。 編譯器後，使用*Ildasm.exe*拆解*Hello.exe*程式集並查看組件資訊清單。

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

在*Hello.exe*程式集上運行命令*ildasm.exe，* 按兩下 MSIL 拆解器視窗中的 **"清單"** 圖示可生成以下輸出：

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

下表描述了示例中使用的*Hello.exe*程式集的組件資訊清單中的每個指令：

|指示詞|描述|
|---------------|-----------------|
|**.程式集外部\<程式集名稱>**|指定另一個組件，其中包含目前模組所參考的項目 (在此範例中為 `mscorlib`)。|
|**.公共鍵權杖\<>**|指定所參考組件之實際金鑰的權杖。|
|**.ver\<版本號>**|指定所參考組件的版本號碼。|
|**.程式集\<名稱>**|指定組件名稱。|
|**.雜湊演算法\<int32 值>**|指定使用的雜湊演算法。|
|**.ver\<版本號>**|指定組件的版本號碼。|
|**.模組\<檔案名>**|指定構成組件之模組的名稱。 在此範例中，組件只包含一個檔案。|
|**.子系統\<值>**|指定程式所需的應用程式環境。 在此範例中，值 3 指出從主控台執行這個可執行檔。|
|**.corflags**|中繼資料中目前保留的欄位。|

根據組件的內容，組件資訊清單可以包含許多不同的指示詞。 有關組件資訊清單中指令的廣泛清單，請參閱 Ecma 文檔，特別是"分區 II：元資料定義和語義"和"分區 III：CIL 指令集"：

- [ECMA C# 和通用語言基礎結構標準](../components.md#applicable-standards)
- [標準 ECMA-335 - 通用語言基礎設施 （CLI）](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a>另請參閱

- [應用程式域和程式集](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [應用程式域和程式集"如何"主題](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md)
