---
title: "在 Visual Basic 中的命名空間 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.global
dev_langs:
- VB
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names, avoiding conflicts
- naming conflicts, namespaces
- namespaces, assemblies
- Visual Basic code, namespaces
- fully qualified names
- naming conventions, naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fe94e65ddbb4ebd2f7d26e8750a0a7ef5d3153af
ms.lasthandoff: 03/13/2017

---
# <a name="namespaces-in-visual-basic"></a>Visual Basic 中的命名空間
命名空間可組織組件中定義的物件。 組件可包含多個命名空間，而命名空間也可包含其他命名空間。 在使用類別庫等大型物件群組時，命名空間可避免語意模糊並簡化參考。  
  
 例如，[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]定義<xref:System.Windows.Forms.ListBox>類別<xref:System.Windows.Forms?displayProperty=fullName>命名空間。</xref:System.Windows.Forms?displayProperty=fullName> </xref:System.Windows.Forms.ListBox> 下列程式碼片段示範如何使用這個類別的完整名稱來宣告變數：  
  
 [!code-vb[VbVbalrApplication #&6;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a>避免名稱衝突  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]命名空間解決問題，有時也稱為*命名空間干擾*，在類別庫的開發人員下滑類似的名稱，另一個文件庫中使用。 這些與現有元件的衝突有時稱為 *「名稱衝突」*(name collision)。  
  
 例如，如果您建立了一個名為 `ListBox`的新類別，您不需提供完整名稱就可以在專案內使用它。 不過，如果您想要使用[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]<xref:System.Windows.Forms.ListBox>類別在相同專案中，您必須使用完整的參考，讓參考唯一。</xref:System.Windows.Forms.ListBox> 如果參考不是唯一的，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會產生錯誤，表示該名稱模稜兩可。 下列程式碼範例示範如何宣告這些物件：  
  
 [!code-vb[VbVbalrApplication #&7;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 下圖顯示兩個命名空間階層，兩者都包含一個名為 `ListBox`的物件。  
  
 ![命名空間階層](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")  
  
 根據預設，每個用 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 建立的可執行檔，都會包含一個與專案同名的命名空間。 例如，如果您在名為 `ListBoxProject`的專案中定義物件，則可執行檔 ListBoxProject.exe 會包含一個稱為 `ListBoxProject`的命名空間。  
  
 多個組件可以使用相同的命名空間。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會將它們視為一個名稱集。 例如，您可以在名為 `Assemb1` 的組件中為稱為 `SomeNameSpace` 的命名空間定義類別，並自一個名為 `Assemb2` 的組件中為相同的命名空間定義其他類別。  
  
## <a name="fully-qualified-names"></a>完整名稱  
 完整名稱是物件參考，前面會加上定義物件之命名空間的名稱。 如果您建立類別的參考 (在 [專案] **** 功能表中選擇 [加入參考] **** )，就可以使用其他專案中所定義的物件，並且在程式碼中使用該物件的完整名稱。 下列程式碼片段示範如何使用另一個專案命名空間之物件的完整名稱：  
  
 [!code-vb[VbVbalrApplication #&8;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 完整名稱可防止命名衝突，因為完整名稱讓編譯器能夠判斷正在使用哪一個物件。 不過，名稱本身可能既長又累贅。 若要解決這個問題，您可以使用 `Imports` 陳述式定義一個 *「別名」*(alias)，也就是可用於取代完整名稱的縮寫名稱。 例如，下列程式碼範例會建立兩個完整名稱的別名，並使用這些別名定義兩個物件。  
  
 [!code-vb[VbVbalrApplication #&9;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication #&10;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 如果您使用沒有別名的 `Imports` 陳述式，則不需要提供完整名稱就可以使用該命名空間中的所有名稱，但前提是這些名稱對於專案而言是唯一的。 如果您的專案所包含的 `Imports` 陳述式與命名空間內的項目有相同名稱，您必須在使用時提供完整名稱。 例如，假設您的專案含有下列兩個 `Imports` 陳述式：  
  
 [!code-vb[VbVbalrApplication #&11;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 如果您嘗試使用 `Class1` 但未提供完整名稱，則 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會產生錯誤，表示名稱 `Class1` 模稜兩可。  
  
## <a name="namespace-level-statements"></a>命名空間層級陳述式  
 在命名空間中，您可以定義模組、介面、類別、委派、列舉、結構和其他命名空間等項目。 您無法在命名空間層級定義屬性、程序、變數和事件等項目。 這些項目必須在模組、結構或類別等容器內宣告。  
  
## <a name="global-keyword-in-fully-qualified-names"></a>完整名稱中的 Global 關鍵字  
 如果您已經定義的命名空間的巢狀的階層，該階層內的程式碼可能會封鎖而無法存取<xref:System?displayProperty=fullName>的.NET Framework 命名空間。</xref:System?displayProperty=fullName> 下列範例會說明階層，在其中`SpecialSpace.System` <xref:System?displayProperty=fullName>.</xref:System?displayProperty=fullName>存取命名空間區塊  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 如此一來，Visual Basic 編譯器無法成功地將參考解析<xref:System.Int32?displayProperty=fullName>，因為`SpecialSpace.System`不會定義`Int32`。</xref:System.Int32?displayProperty=fullName> 您可以使用 `Global` 關鍵字，在 .NET Framework 類別庫的最外層啟動限定性鏈結。 這可讓您指定<xref:System?displayProperty=fullName>命名空間或類別庫中的任何其他命名空間。</xref:System?displayProperty=fullName> 下列範例將說明這點。  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 您可以使用`Global`來存取其他根層級命名空間，例如<xref:Microsoft.VisualBasic?displayProperty=fullName>，和任何與您的專案相關聯的命名空間。</xref:Microsoft.VisualBasic?displayProperty=fullName>  
  
## <a name="global-keyword-in-namespace-statements"></a>Namespace 陳述式中的 Global 關鍵字  
 您也可以使用`Global`關鍵字[命名空間陳述式](../../../visual-basic/language-reference/statements/namespace-statement.md)。 這可讓您從專案的根命名空間定義一個命名空間。  
  
 專案中的所有命名空間都會以專案的根命名空間為基礎。  Visual Studio 會針對專案中的所有程式碼，將專案名稱指派為預設根命名空間。 例如，如果專案已命名為 `ConsoleApplication1`，其程式設計項目會屬於命名空間 `ConsoleApplication1`。 如果您宣告 `Namespace Magnetosphere`，專案中的 `Magnetosphere` 參考可存取 `ConsoleApplication1.Magnetosphere`。  
  
 下列範例使用 `Global` 關鍵字，從專案的根命名空間宣告一個命名空間。  
  
 [!code-vb[VbVbalrApplication #&22;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 在命名空間宣告中， `Global` 不能以巢狀方式放在另一個命名空間中。  
  
 您可以使用[應用程式] 頁面上，[專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)來檢視和修改**根命名空間**的專案。  若是新專案，[根命名空間] **** 預設為專案名稱。 若要使 `Global` 成為最上層命名空間，您可以清除 [根命名空間] **** 項目讓方塊空白。 清除 [根命名空間] **** 就不再需要命名空間宣告中的 `Global` 關鍵字。  
  
 如果 `Namespace` 陳述式所宣告的名稱也是 .NET Framework 中的命名空間，當完整名稱中未使用 `Global` 關鍵字時，.NET Framework 命名空間會變成無法使用。 若要允許在不使用 `Global` 關鍵字的情況下存取該 .NET Framework 命名空間，您可以在 `Global` 陳述式中包含 `Namespace` 關鍵字。  
  
 下列範例在 `Global` 命名空間宣告中有 `System.Text` 關鍵字。  
  
 如果`Global`關鍵字不存在於命名空間宣告，<xref:System.Text.StringBuilder>無法存取而不指定`Global.System.Text.StringBuilder`。</xref:System.Text.StringBuilder> 針對名為 `ConsoleApplication1`的專案，如果未使用 `System.Text` 關鍵字， `ConsoleApplication1.System.Text` 的參考會存取 `Global` 。  
  
 [!code-vb[VbVbalrApplication #&21;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ListBox></xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms?displayProperty=fullName></xref:System.Windows.Forms?displayProperty=fullName>   
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [如何︰ 建立和使用組件︰ 使用命令列](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)   
 [參考和 Imports 陳述式](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [撰寫 Office 方案中的程式碼](https://msdn.microsoft.com/library/bb608596)
