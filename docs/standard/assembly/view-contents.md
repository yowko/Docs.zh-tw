---
title: HOW TO：視圖元件內容
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
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 8f27afafde0b83dfe886d218f3148d8ff07b30cb
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973023"
---
# <a name="how-to-view-assembly-contents"></a>作法：視圖元件內容
您可以使用 [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md) 來檢視檔案中的 Microsoft 中繼語言 (MSIL) 資訊。 如果所檢查的檔案是組件，這項資訊可以包括組件的屬性，以及其他模組和組件的參考。 這項資訊可能有助於判斷檔案是組件還是組件的一部分，以及檔案是否有其他模組或組件的參考。  
  
若要使用*Ildasm*顯示元件的內容，請在命令提示字元中輸入**Ildasm** \<*元件名稱*>。 例如，下列命令會反組譯*Hello .exe*元件。  

```cmd
ildasm Hello.exe  
```  

若要查看組件資訊清單資訊，請按兩下 [MSIL 解譯器] 視窗中的**資訊清單**圖示。  
  
## <a name="example"></a>範例  
下列範例會從基本的「Hello World」程式開始。 編譯器之後，請使用*Ildasm*來拆解 *.exe*元件，並查看組件資訊清單。  

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
Imports System

Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

在 *.exe*元件*上執行*命令 tlbimp.exe，然後按兩下 [MSIL 解譯器] 視窗中的**資訊清單**圖示，會產生下列輸出：  

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
  
 下表描述範例中所使用之*Hello .exe*元件的組件資訊清單中的每個指示詞。  
  
|指示詞|描述|  
|---------------|-----------------|  
|**.assembly extern \<**  *組件名稱* **>**|指定另一個組件，其中包含目前模組所參考的項目 (在此範例中為 `mscorlib`)。|  
|**.publickeytoken \<**  *語彙基元* **>**|指定所參考組件之實際金鑰的權杖。|  
|**.ver \<**  *版本號碼* **>**|指定所參考組件的版本號碼。|  
|**.assembly \<**  *組件名稱* **>**|指定組件名稱。|  
|**.hash algorithm \<**  *int32 值* **>**|指定使用的雜湊演算法。|  
|**.ver \<**  *版本號碼* **>**|指定組件的版本號碼。|  
|**.module \<**  *檔案名稱* **>**|指定構成組件之模組的名稱。 在此範例中，組件只包含一個檔案。|  
|**.subsystem \<**  *值* **>**|指定程式所需的應用程式環境。 在此範例中，值 3 指出從主控台執行這個可執行檔。|  
|**.corflags**|中繼資料中目前保留的欄位。|  
  
 根據組件的內容，組件資訊清單可以包含許多不同的指示詞。 如需組件資訊清單中的指示詞延伸清單，請參閱 ECMA 文件，特別是 "Partition II:Metadata Definition and Semantics" 和 "Partition III:CIL 指令集。」 檔可在線上取得。 請參閱 MSDN 上的[ecma C#和通用語言基礎結構標準](https://go.microsoft.com/fwlink/?LinkID=99212)，以及 ecma 國際網站上的[標準 Ecma-335-通用語言基礎結構（CLI）](https://go.microsoft.com/fwlink/?LinkID=65552) 。  
  
## <a name="see-also"></a>另請參閱

- [應用程式定義域和組件](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [應用程式域和元件的 how to 主題](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md)
