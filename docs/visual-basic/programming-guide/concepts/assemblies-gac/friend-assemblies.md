---
title: Friend 組件 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
ms.openlocfilehash: 9b91f894f9b10c85eb322b4421fd0473335df7a3
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748150"
---
# <a name="friend-assemblies-visual-basic"></a>Friend 組件 (Visual Basic)
A *friend 組件*是可以存取另一個組件的組件[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)類型和成員。 如果將組件指定為 friend 組件，就不再需要將類型和成員標記為 public，以供其他組件存取。 這在下列情況下特別方便：  
  
-   在單元測試，在中執行的測試程式碼時個別的組件但需要存取所測試的組件中的成員標記為`Friend`。  
  
-   當您正在開發的類別庫和程式庫的新增項目包含在個別的組件，但需要標示為的現有組件中的成員存取`Friend`。  
  
## <a name="remarks"></a>備註  
 您可以使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性找出指定組件的一或多個 Friend 組件。 下列範例會使用組件 A 中的 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性，並將組件 `AssemblyB` 指定為 Friend 組件。 這可讓組件 `AssemblyB` 存取組件 A 中所有標記為 `Friend` 的類型和成員。  
  
> [!NOTE]
>  如果您編譯的組件 (組件 `AssemblyB`) 會存取另一個組件 (組件 *A*) 的內部類型或內部成員，您必須使用 **/out** 編譯器選項明確指定輸出檔案的名稱 (.exe 或 .dll)。 因為編譯器尚未針對在繫結至外部參考時所建立的組件產生名稱，所以這是必要動作。 如需詳細資訊，請參閱 < [/輸出 (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)。  
  
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
  
 只有明確指定為 friend 的組件才能存取 `Friend` 類型和成員。 例如，如果組件 B 是組件 A 的 friend，而且組件 C 參考組件 B，則 C 無法存取 A 中的 `Friend` 類型。  
  
 編譯器會執行一些被傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱的基本驗證。 如果組件 *A* 將 *B* 宣告為 friend 組件，則驗證規則如下：  
  
-   如果組件 *A* 具有強式名稱，則組件 *B* 也必須具有強式名稱。 傳遞給這個屬性的 friend 組件名稱必須包含組件名稱，以及簽署組件 *B* 時所用強式名稱金鑰的公開金鑰。  
  
     傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的 Friend 組件名稱不能是組件 *B* 的強式名稱：請勿包含組件版本、文化特性、架構或公開金鑰語彙基元。  
  
-   如果組件 *A* 不具強式名稱，friend 組件名稱只應包含組件名稱。 如需詳細資訊，請參閱[如何：建立未簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)。  
  
-   如果組件 *B* 具有強式名稱，您必須使用專案設定或命令列的 `/keyfile` 編譯器選項，為組件 *B* 指定強式名稱金鑰。 如需詳細資訊，請參閱[如何：建立簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)。  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission> 類別也會提供共用類型的功能，但有下列差異：  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission> 適用於個別類型，而 Friend 組件適用於整個組件。  
  
-   如果要將組件 *A* 中數百個類型與組件 *B* 共用，必須將 <xref:System.Security.Permissions.StrongNameIdentityPermission> 新增至所有類型。 如果使用 friend 組件，您只需要宣告 friend 關聯性一次。  
  
-   如果您使用 <xref:System.Security.Permissions.StrongNameIdentityPermission>，則您想要共用的類型必須宣告為公用。 如果使用 friend 組件，共用的類型會宣告為 `Friend`。  
  
 如需有關如何存取組件的資訊`Friend`型別和方法，從模組檔案 （副檔名為.netmodule 檔案），請參閱[/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [如何：建立未簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [如何：建立簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [在.NET 中的組件](../../../../standard/assembly/index.md)
- [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)
