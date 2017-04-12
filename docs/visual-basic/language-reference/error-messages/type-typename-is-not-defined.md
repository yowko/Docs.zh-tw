---
title: "類型 &quot;&lt;typename&gt;&quot; 未定義 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
dev_langs:
- VB
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 09aa7c535fd5e17ddcd0e743fb5ec17ebadd4f7d
ms.lasthandoff: 03/13/2017

---
# <a name="type-39lttypenamegt39-is-not-defined"></a>類型 '&lt;typename&gt;' 未定義
陳述式已參考未定義的型別。 您可以定義中宣告陳述式的類型例如`Enum`， `Structure`， `Class`，或`Interface`。  
  
 **錯誤識別碼︰** BC30002  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定型別定義和它的參考都使用相同的拼字。  
  
-   確定型別定義可存取的參考。 例如，如果型別是在另一個模組，而且已宣告`Private`、 將型別定義移至參考的模組，或將它宣告`Public`。  
  
-   請確定型別的命名空間不會重新定義您專案中。 如果是，使用`Global`關鍵字來完整限定的型別名稱。 例如，如果專案定義的命名空間，且`System`、<xref:System.Object?displayProperty=fullName>無法存取型別，除非它是以完整限定`Global`關鍵字︰ `Global.System.Object`。</xref:System.Object?displayProperty=fullName>  
  
-   如果型別定義，但物件程式庫或在其中定義的型別程式庫未登錄在[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，按一下 [**加入參考**上**專案**] 功能表上，然後選取適當的物件程式庫或型別程式庫。  
  
-   確定為目標的.NET Framework 設定檔的一部分的組件中的型別。 如需詳細資訊，請參閱[疑難排解.NET Framework 目標錯誤](https://docs.microsoft.com/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [管理專案中的參考](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)
