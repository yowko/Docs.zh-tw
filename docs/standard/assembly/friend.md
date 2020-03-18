---
title: Friend 組件
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: a74d4b74ead8492028a092e090f9281231802a87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348170"
---
# <a name="friend-assemblies"></a>Friend 組件

*友用程式集*是可以訪問其他程式集[的內部](../../csharp/language-reference/keywords/internal.md)（C#） 或[Friend（](../../visual-basic/language-reference/modifiers/friend.md)可視基本）類型和成員的程式集。 如果將組件指定為 friend 組件，就不再需要將類型和成員標記為 public，以供其他組件存取。 這在下列情況下特別方便：

- 在單元測試期間，當測試程式碼在另一個組件中執行，但需要存取所測試組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。

- 當您要開發類別庫且類別庫的新增項目包含在不同的組件，但需要存取現有組件中標記為 `internal` (C#) 或 `Friend` (Visual Basic) 的成員時。

## <a name="remarks"></a>備註

您可以使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性找出指定組件的一或多個 Friend 組件。 下面的示例使用程式集<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>*A*中的屬性，並將*程式集 B*指定為友用程式集。 這使程式集*B*能夠訪問*程式集 A*中標記為`internal`C# 或視覺化基本版中的所有`Friend`類型和成員。

> [!NOTE]
> 編譯器集（如*AssemblyB）* 以訪問程式集*A*等其他程式集的內部類型或內部成員時，必須使用 **-out**編譯器選項顯式指定輸出檔案 *（.exe*或 *.dll）* 的名稱。 因為編譯器尚未針對在繫結至外部參考時所建立的組件產生名稱，所以這是必要動作。 有關詳細資訊，請參閱[-out （C#）](../../csharp/language-reference/compiler-options/out-compiler-option.md)或[-out （可視基本）](../../visual-basic/reference/command-line-compiler/out.md)。

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

只有您明確指定為好友的程式集才能訪問`internal`（C#）`Friend`或（可視基本）類型和成員。 例如，如果*程式集 B*是程式集*A*的友，*程式集 C*引用程式集*B，**則程式集 C*不能訪問`Friend`*Assembly A*`internal`程式集 A 中的 （C#） 或 （可視基本）類型。

編譯器會執行一些被傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱的基本驗證。 如果*程式集 A*聲明*程式集 B*為友用程式集，則驗證規則如下所示：

- 如果*程式集 A*具有強式名稱，*則程式集 B*也必須強命名。 傳遞給屬性的友元程式集名稱必須包含程式集名稱和用於對*AssemblyB*進行簽名的強式名稱鍵的公開金鑰。

     傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>該屬性的友元程式集名稱不能是*程式集 B*的強式名稱。 不包括程式集版本、區域性、體系結構或公開金鑰權杖。

- 如果*程式集 A*不是強式名稱，則友號程式集名稱應僅包含程式集名稱。 有關詳細資訊，請參閱[如何：創建未簽名的好友程式集](create-unsigned-friend.md)。

- 如果*程式集 B*是強式名稱，則必須通過使用專案設置或命令列*AssemblyB*`/keyfile`編譯器選項為程式集 B 指定強式名稱鍵。 有關詳細資訊，請參閱[：創建已簽名的好友程式集](create-signed-friend.md)。

 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別也會提供共用類型的功能，但有下列差異：

- <xref:System.Security.Permissions.StrongNameIdentityPermission> 適用於個別類型，而 Friend 組件適用於整個組件。

- 如果要與*程式集 B*共用*程式集 A*中有數百種類型，則必須將它們添加到<xref:System.Security.Permissions.StrongNameIdentityPermission>所有類型中。 如果使用 friend 組件，您只需要宣告 friend 關聯性一次。

- 如果您使用 <xref:System.Security.Permissions.StrongNameIdentityPermission>，則您想要共用的類型必須宣告為公用。 如果使用友元程式集，則共用類型將聲明為`internal`（C#） 或`Friend`（可視基本）。

有關如何從模組檔（具有 *.netmodule*副檔名的檔）`Friend`訪問程式集 （C#）`internal`或（可視基本）類型和方法的資訊，請參閱[-模組程式集名稱 （C#）](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)或[-模組程式集名稱 （可視基本名稱）。](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [如何：創建未簽名的好友程式集](create-unsigned-friend.md)
- [如何：創建簽名的好友程式集](create-signed-friend.md)
- [.NET 中的組件](index.md)
- [C# 程式設計指南](../../csharp/programming-guide/index.md)
- [程式設計概念（視覺基礎）](../../visual-basic/programming-guide/concepts/index.md)
