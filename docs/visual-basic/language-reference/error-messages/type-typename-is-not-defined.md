---
title: 型別&#39; &lt;typename&gt; &#39;未定義
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7c3efbcabf1e40c7f550b5f54d16e697561cf82c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="type-39lttypenamegt39-is-not-defined"></a>型別&#39; &lt;typename&gt; &#39;未定義
陳述式已參考未定義的類型。 您可以定義宣告陳述式中的類型例如`Enum`， `Structure`， `Class`，或`Interface`。  
  
 **錯誤 ID:** BC30002  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定類型定義，而且它的參考都使用相同的拼字。  
  
-   確定參考可存取的類型定義。 例如，如果類型是在另一個模組並已宣告`Private`、 將參考的模組類型定義，或將它宣告`Public`。  
  
-   請確定型別的命名空間不在專案中重新定義。 如果是，使用`Global`關鍵字來完整限定類型名稱。 例如，如果專案定義名為的命名空間`System`、<xref:System.Object?displayProperty=nameWithType>無法存取類型，除非它是使用完整限定`Global`關鍵字： `Global.System.Object`。  
  
-   如果類型定義，但在定義的型別程式庫的物件程式庫未登錄在 Visual Basic 中，按一下**加入參考**上**專案** 功能表，然後選取適當的物件程式庫或類型程式庫。  
  
-   請為目標的.NET Framework 設定檔一部分的組件中的類型。 如需詳細資訊，請參閱[針對 .NET Framework 目標錯誤進行疑難排解](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)
