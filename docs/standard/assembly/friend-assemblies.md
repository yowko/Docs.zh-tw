---
title: Friend 組件 (C#)
ms.date: 03/03/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: 770eb70a5350d7d26e03cb4e605b442100da2a53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68671193"
---
# <a name="friend-assemblies"></a>Friend 組件

「Friend 組件」  是可以存取另一個組件的 [internal](../../csharp/language-reference/keywords/internal.md) (C#，或 Visual Basic 中的 [Friend](../../visual-basic/language-reference/modifiers/friend.md)) 型別和成員組件。 如果將組件指定為 friend 組件，就不再需要將類型和成員標記為 public，以供其他組件存取。 這在下列情況下特別方便：

- 在單元測試期間，當測試程式碼在另一個組件中執行，但需要存取所測試組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。

- 當您要開發類別庫且類別庫的新增項目包含在不同的組件，但需要存取現有組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。

## <a name="remarks"></a>備註

您可以使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性找出指定組件的一或多個 Friend 組件。 下列範例會使用組件 A 中的 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性，並將組件 `AssemblyB` 指定為 Friend 組件。 這可讓組件 `AssemblyB` 存取組件 A 中所有標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的型別和成員。

> [!NOTE]
> 如果您編譯的組件 (組件 `AssemblyB`) 會存取另一個組件 (組件 *A*) 的內部類型或內部成員，您必須使用 **/out** 編譯器選項明確指定輸出檔案的名稱 (.exe 或 .dll)。 因為編譯器尚未針對在繫結至外部參考時所建立的組件產生名稱，所以這是必要動作。 如需詳細資訊，請參閱 [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) 或 [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

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

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

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

---

只有明確指定為 Friend 的組件才能存取 `internal` (C#，或 Visual Basic 中的 `Friend`) 類型和成員。 例如，如果組件 B 是組件 A 的 Friend，且組件 C 參考組件 B，則 C 無法存取 A 中的 `internal` (C#，或 Visual Basic 中的 `Friend`) 型別。

編譯器會執行一些被傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱的基本驗證。 如果組件 *A* 將 *B* 宣告為 friend 組件，則驗證規則如下：

- 如果組件 *A* 具有強式名稱，則組件 *B* 也必須具有強式名稱。 傳遞給這個屬性的 friend 組件名稱必須包含組件名稱，以及簽署組件 *B* 時所用強式名稱金鑰的公開金鑰。

     傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱不能是組件 *B* 的強式名稱：請勿包含組件版本、文化特性、架構或公開金鑰語彙基元。

- 如果組件 *A* 不具強式名稱，friend 組件名稱只應包含組件名稱。 如需詳細資訊，請參閱[如何：建立未簽署的 Friend 組件 (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) 或[如何：建立未簽署的 Friend 組件 (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)。

- 如果組件 *B* 具有強式名稱，您必須使用專案設定或命令列的 `/keyfile` 編譯器選項，為組件 *B* 指定強式名稱金鑰。 如需詳細資訊，請參閱[如何：建立簽署的 Friend 組件 (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) 或[如何：建立簽署的 Friend 組件 (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)。

 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別也會提供共用類型的功能，但有下列差異：

- <xref:System.Security.Permissions.StrongNameIdentityPermission> 適用於個別類型，而 Friend 組件適用於整個組件。

- 如果要將組件 *A* 中數百個類型與組件 *B* 共用，必須將 <xref:System.Security.Permissions.StrongNameIdentityPermission> 新增至所有類型。 如果使用 friend 組件，您只需要宣告 friend 關聯性一次。

- 如果您使用 <xref:System.Security.Permissions.StrongNameIdentityPermission>，則您想要共用的類型必須宣告為公用。 如果使用 Friend 組件，共用型別會宣告為 `internal` (C#，或 Visual Basic 中的 `Friend`)。

如需如何從從模組檔 (副檔名為 .netmodule 的檔案) 存取組件的 `internal` (C#,或 Visual Basic 中的 `Friend`) 型別和方法資訊，請參閱 [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) 或 [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [如何：建立未簽署的 Friend 組件 (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [如何：建立未簽署的 Friend 組件 (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [如何：建立簽署的 Friend 組件 (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [如何：建立簽署的 Friend 組件 (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [.NET 中的組件](index.md)
- [C# 程式設計指南](../../csharp/programming-guide/index.md)
- [程式設計概念](../../visual-basic/programming-guide/concepts/index.md)
