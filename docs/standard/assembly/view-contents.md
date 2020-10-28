---
title: 如何：查看元件內容
description: 您可以使用 IL 解譯器來查看元件的屬性，以及其他模組和元件的參考。
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: be2311c601effbebd519e33b7a5e13d49f44bd05
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687498"
---
# <a name="how-to-view-assembly-contents"></a>如何：查看元件內容

您可以使用 [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md) 來檢視檔案中的 Microsoft 中繼語言 (MSIL) 資訊。 如果要檢查的檔案是元件，這項資訊可以包含元件的屬性以及其他模組和元件的參考。 這項資訊有助於判斷檔案是元件或元件的一部分，以及檔案是否有其他模組或元件的參考。

若要使用 *Ildasm.exe* 顯示元件的內容，請在命令提示字元中輸入 **ildasm \<assembly name>** 。 例如，下列命令會反組解碼 *Hello.exe* 元件。

```cmd
ildasm Hello.exe
```

若要查看組件資訊清單資訊，請按兩下 [MSIL 解譯器] 視窗中的 **資訊清單** 圖示。

## <a name="example"></a>範例

下列範例會從基本的 "Hello World" 程式開始。 編譯器之後，請使用 *Ildasm.exe* 來拆解 *Hello.exe* 元件，並查看組件資訊清單。

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

在 *Hello.exe* 元件上執行命令 *ildasm.exe* ，然後按兩下 [MSIL 解譯器] 視窗中的 **資訊清單** 圖示，就會產生下列輸出：

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

下表描述範例中所使用 *Hello.exe* 元件的組件資訊清單中的每個指示詞：

|指示詞|描述|
|---------------|-----------------|
|**。元件 extern \<assembly name>**|指定另一個組件，其中包含目前模組所參考的項目 (在此範例中為 `mscorlib`)。|
|**publickeytoken \<token>**|指定所參考組件之實際金鑰的權杖。|
|**ver \<version number>**|指定所參考組件的版本號碼。|
|**. 元件 \<assembly name>**|指定組件名稱。|
|**雜湊演算法 \<int32 value>**|指定使用的雜湊演算法。|
|**ver \<version number>**|指定組件的版本號碼。|
|**。模組 \<file name>**|指定構成組件之模組的名稱。 在此範例中，組件只包含一個檔案。|
|**。子系統 \<value>**|指定程式所需的應用程式環境。 在此範例中，值 3 指出從主控台執行這個可執行檔。|
|**.corflags**|中繼資料中目前保留的欄位。|

根據組件的內容，組件資訊清單可以包含許多不同的指示詞。 如需組件資訊清單中之指示詞的詳盡清單，請參閱 Ecma 檔，特別是「資料分割 II：元資料定義和語義」和「資料分割 III： CIL 指令集」：

- [ECMA c # 和通用語言基礎結構標準](../components.md#applicable-standards)
- [標準 ECMA-335-通用語言基礎結構 (CLI) ](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a>請參閱

- [應用程式定義域和組件](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [應用程式域和元件的 how to 主題](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (IL 解譯器) ](../../framework/tools/ildasm-exe-il-disassembler.md)
