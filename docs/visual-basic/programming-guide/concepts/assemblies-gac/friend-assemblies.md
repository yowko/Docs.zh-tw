---
title: "Friend 組件 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c6e01ae91b9d5d875bb618993cd9eda82db59399
ms.lasthandoff: 03/13/2017

---
# <a name="friend-assemblies-visual-basic"></a>Friend 組件 (Visual Basic)
A *friend 組件*是可以存取另一個組件的組件[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)型別和成員。 如果您找出組件做為 friend 組件，您不再需要標記型別和成員為公用，才會由其他組件存取。 這是非常方便您在下列情況︰  
  
-   在單元測試，測試程式碼中執行時不同的組件，但是需要標示為正在測試的組件中的成員存取`Friend`。  
  
-   當您正在開發的類別程式庫和程式庫的新增項目都包含在不同的組件，但需要標示為的現有組件中的成員存取`Friend`。  
  
## <a name="remarks"></a>備註  
 您可以使用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性來識別指定的組件的一或多個 friend 組件。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 下列範例會使用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性在組件 A 中，指定組件`AssemblyB`做為 friend 組件。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 這可讓組件`AssemblyB`所有型別和組件中，標示為成員存取`Friend`。  
  
> [!NOTE]
>  當您編譯組件 (組件`AssemblyB`)，將存取內部型別或內部成員的另一個組件 (組件*A*)，您必須使用明確指定輸出檔 （.exe 或.dll） 的名稱**/輸出**編譯器選項。 這是必要的因為編譯器但尚未產生它所繫結至外部參考時，它本身正在建置的組件的名稱。 如需詳細資訊，請參閱[/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)。  
  
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
  
 只有明確指定的朋友可以存取的組件`Friend`型別和成員。 例如，如果組件 A 和組件 C 參考組件 B 的 friend 組件 B，C 並沒有存取權`Friend`a 中的型別  
  
 編譯器會執行一些基本驗證的 friend 組件名稱傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 如果組件*A*宣告*B*做為 friend 組件中，驗證規則如下︰  
  
-   如果組件*A*具有強式名稱，組件*B*也必須強式名稱。 Friend 組件名稱傳遞給該屬性必須包含組件名稱以及用來簽署組件的強式名稱金鑰的公開金鑰*B*。  
  
     Friend 組件名稱傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性不能為組件的強式名稱*B*︰ 不包含組件版本、 文化特性、 架構或公開金鑰語彙基元。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
  
-   如果組件*A*不是強式命名組件名稱應該包含 friend 組件名稱。 如需詳細資訊，請參閱[How to︰ 建立未簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)。  
  
-   如果組件*B*具有強式名稱，您必須指定組件的強式名稱金鑰*B*的專案設定，或是在命令列使用`/keyfile`編譯器選項。 如需詳細資訊，請參閱[How to︰ 建立簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)。  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>類別也提供共用型別，但有下列差異︰</xref:System.Security.Permissions.StrongNameIdentityPermission>  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission>雖然 friend 組件適用於整個組件適用於個別的型別。</xref:System.Security.Permissions.StrongNameIdentityPermission>  
  
-   如果有數百個組件中的型別*A*您想要分享的組件*B*，您必須加入<xref:System.Security.Permissions.StrongNameIdentityPermission>至所有端點。</xref:System.Security.Permissions.StrongNameIdentityPermission> 如果您使用 friend 組件，您只需要一次宣告的 friend 關聯性。  
  
-   如果您使用<xref:System.Security.Permissions.StrongNameIdentityPermission>，您想要共用的類型必須宣告為公用。</xref:System.Security.Permissions.StrongNameIdentityPermission> 如果您使用 friend 組件時，共用的類型會宣告為`Friend`。  
  
 如需有關如何存取組件的資訊`Friend`型別和方法，從模組檔案 （副檔名為.netmodule 檔案），請參閱[/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 <xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Security.Permissions.StrongNameIdentityPermission>   
 [如何︰ 建立未簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)   
 [如何︰ 建立已簽署的 Friend 組件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)
