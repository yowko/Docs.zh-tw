---
title: Friend 組件
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: 6387e93bcd4efeec57ada9228dcaf015d053dbf7
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973233"
---
# <a name="friend-assemblies"></a>Friend 組件

*Friend 元件*是一種元件，可以存取另一個元件的[內部](../../csharp/language-reference/keywords/internal.md)C#（）或 [friend](../../visual-basic/language-reference/modifiers/friend.md) （Visual Basic）類型和成員。 如果將組件指定為 friend 組件，就不再需要將類型和成員標記為 public，以供其他組件存取。 這在下列情況下特別方便：

- 在單元測試期間，當測試程式碼在另一個組件中執行，但需要存取所測試組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。

- 當您要開發類別庫且類別庫的新增項目包含在不同的組件，但需要存取現有組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。

## <a name="remarks"></a>備註

您可以使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性找出指定組件的一或多個 Friend 組件。 下列範例會使用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> *元件 A*中的屬性，並將元件*AssemblyB*指定為 friend 元件。 這可讓元件*AssemblyB*存取*元件 A*中的所有類型和成員，並將`internal`其C#標示為 Visual Basic 中的或`Friend` 。

> [!NOTE]
> 當您編譯的元件（例如*AssemblyB* ）將存取另一個元件的內部類型或內部成員（例如*元件 A*）時，您必須使用/out 明確指定輸出檔（ *.exe*或 *.dll*）的名稱。編譯器選項。 因為編譯器尚未針對在繫結至外部參考時所建立的組件產生名稱，所以這是必要動作。 如需詳細資訊，請參閱 [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) 或 [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)。

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
Imports System
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

只有明確指定為 friend 的元件可以存取`internal` （C#）或`Friend` （Visual Basic）類型和成員。 例如，如果*AssemblyB*是*元件 a*的 friend，而*元件 c*參考*AssemblyB*，則*元件 c*無法`internal`存取元件 a 中的（C#） `Friend`或（Visual Basic）類型.

編譯器會執行一些被傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱的基本驗證。 如果*元件 A*宣告*AssemblyB*為 friend 元件，則驗證規則如下所示：

- 如果*元件 A*是強式名稱，則*AssemblyB*也必須是強式名稱。 傳遞至屬性的 friend 元件名稱必須包含用來簽署*AssemblyB*之強式名稱金鑰的元件名稱和公開金鑰。

     傳遞至<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性的 friend 元件名稱不可以是*AssemblyB*的強式名稱。 請勿包含元件版本、文化特性、架構或公開金鑰 token。

- 如果*元件 A*不是強式名稱，friend 元件名稱應該只包含元件名稱。 如需詳細資訊，請參閱[如何：建立未簽署的](create-unsigned-friend.md)friend 元件。

- 如果*AssemblyB*是強式名稱，您必須使用專案設定或命令列`/keyfile`編譯器選項，為*AssemblyB*指定強式名稱索引鍵。 如需詳細資訊，請參閱[如何：建立已簽署的](create-signed-friend.md)friend 元件。

 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別也會提供共用類型的功能，但有下列差異：

- <xref:System.Security.Permissions.StrongNameIdentityPermission> 適用於個別類型，而 Friend 組件適用於整個組件。

- 如果您想要與*AssemblyB*共用的<xref:System.Security.Permissions.StrongNameIdentityPermission> *元件 A*中有數百個類型，您必須將新增至所有專案。 如果使用 friend 組件，您只需要宣告 friend 關聯性一次。

- 如果您使用 <xref:System.Security.Permissions.StrongNameIdentityPermission>，則您想要共用的類型必須宣告為公用。 如果您使用 friend 元件，共用的類型會宣告為`internal` （C#）或`Friend` （Visual Basic）。

如需如何從模組檔案（副檔名為`internal` *.netmodule*的檔案`Friend` ）存取元件（C#）或（Visual Basic）類型和方法的詳細資訊，請參閱[/moduleassemblyname （C#）](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)或[/moduleassemblyname （Visual Basic）](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [如何：建立未簽署的 friend 元件](create-unsigned-friend.md)
- [如何：建立已簽署的 friend 元件](create-signed-friend.md)
- [.NET 中的組件](index.md)
- [C# 程式設計指南](../../csharp/programming-guide/index.md)
- [程式設計概念（Visual Basic）](../../visual-basic/programming-guide/concepts/index.md)
