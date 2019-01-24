---
title: 類型&#39; &lt;typename&gt; &#39;未定義
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 8e303a9ac6529fbbc818c94497a16463897fb0c5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496123"
---
# <a name="type-39lttypenamegt39-is-not-defined"></a>類型&#39; &lt;typename&gt; &#39;未定義
陳述式已參考了尚未定義的類型。 您可以定義在宣告陳述式類型這類`Enum`， `Structure`， `Class`，或`Interface`。  
  
 **錯誤 ID:** BC30002  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定類型定義，而且它的參考都使用相同的拼字。  
  
-   確定存取參考的型別定義。 例如，如果類型是在另一個模組，而且已宣告`Private`、 將型別定義移至參考的模組，或將它宣告`Public`。  
  
-   請確定類型的命名空間不會重新定義您的專案內。 如果是，使用`Global`關鍵字來完整限定的型別名稱。 例如，如果專案定義名為命名空間`System`，則<xref:System.Object?displayProperty=nameWithType>無法存取類型，除非它是以完整限定`Global`關鍵字： `Global.System.Object`。  
  
-   如果類型定義，但在 Visual Basic 中，按一下的物件程式庫或在其中定義的型別程式庫未註冊**加入參考**上**專案**功能表、，然後選取適當的物件程式庫或型別程式庫。  
  
-   請確定類型位於組件的目標.NET Framework 設定檔的一部分。 如需詳細資訊，請參閱[針對 .NET Framework 目標錯誤進行疑難排解](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)。  
  
## <a name="see-also"></a>另請參閱
- [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)
- [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)
- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)
