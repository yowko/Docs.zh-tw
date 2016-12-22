---
title: "Visual Basic 中的命名空間 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.global"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "組件 [Visual Basic], 命名空間"
  - "名稱衝突"
  - "Global 關鍵字 [Visual Basic]"
  - "命名空間干擾"
  - "名稱, 避免衝突"
  - "命名衝突, 命名空間"
  - "命名空間, 組件"
  - "Visual Basic 程式碼, 命名空間"
  - "完整名稱"
  - "命名慣例, 命名衝突"
  - "命名空間"
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Visual Basic 中的命名空間
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

命名空間可組織組件中定義的物件。 組件可包含多個命名空間，而命名空間也可包含其他命名空間。 在使用類別庫等大型物件群組時，命名空間可避免語意模糊並簡化參考。  
  
 例如，[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 會在 <xref:System.Windows.Forms?displayProperty=fullName> 命名空間中定義 <xref:System.Windows.Forms.ListBox> 類別。 下列程式碼片段示範如何使用這個類別的完整名稱來宣告變數：  
  
 [!CODE [VbVbalrApplication#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrApplication#6)]  
  
## 避免名稱衝突  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 命名空間會解決有時稱為*「命名空間干擾」*\(namespace pollution\) 的問題，也就是類別庫的開發人員因為使用與另一個程式庫類似的名稱而受到阻礙的情況。 這些與現有元件的衝突有時稱為*「名稱衝突」*\(name collision\)。  
  
 例如，如果您建立了一個名為 `ListBox` 的新類別，您不需提供完整名稱就可以在專案內使用它。 不過，如果您想在同一個專案中使用 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]<xref:System.Windows.Forms.ListBox> 類別，則必須使用完整參考使其成為唯一的參考。 如果參考不是唯一的，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會產生錯誤，表示該名稱模稜兩可。 下列程式碼範例示範如何宣告這些物件：  
  
 [!CODE [VbVbalrApplication#7](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrApplication#7)]  
  
 下圖顯示兩個命名空間階層，兩者都包含一個名為 `ListBox` 的物件。  
  
 ![命名空間階層架構](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.png "vaNamespaceHierarchy")  
  
 根據預設，每個用 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 建立的可執行檔，都會包含一個與專案同名的命名空間。 例如，如果您在名為 `ListBoxProject` 的專案中定義物件，則可執行檔 ListBoxProject.exe 會包含一個稱為 `ListBoxProject` 的命名空間。  
  
 多個組件可以使用相同的命名空間。[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會將它們視為一個名稱集。 例如，您可以在名為 `Assemb1` 的組件中為稱為 `SomeNameSpace` 的命名空間定義類別，並自一個名為 `Assemb2` 的組件中為相同的命名空間定義其他類別。  
  
## 完整名稱  
 完整名稱是物件參考，前面會加上定義物件之命名空間的名稱。 如果您建立類別的參考 \(在 \[專案\] 功能表中選擇 \[加入參考\]\)，就可以使用其他專案中所定義的物件，並且在程式碼中使用該物件的完整名稱。 下列程式碼片段示範如何使用另一個專案命名空間之物件的完整名稱：  
  
 [!CODE [VbVbalrApplication#8](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrApplication#8)]  
  
 完整名稱可防止命名衝突，因為完整名稱讓編譯器能夠判斷正在使用哪一個物件。 不過，名稱本身可能既長又累贅。 若要解決這個問題，您可以使用 `Imports` 陳述式定義一個*「別名」*\(alias\)，也就是可用於取代完整名稱的縮寫名稱。 例如，下列程式碼範例會建立兩個完整名稱的別名，並使用這些別名定義兩個物件。  
  
 [!CODE [VbVbalrApplication#9](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrApplication#9)]  
  
 [!CODE [VbVbalrApplication#10](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrApplication#10)]  
  
 如果您使用沒有別名的 `Imports` 陳述式，則不需要提供完整名稱就可以使用該命名空間中的所有名稱，但前提是這些名稱對於專案而言是唯一的。 如果您的專案所包含的 `Imports` 陳述式與命名空間內的項目有相同名稱，您必須在使用時提供完整名稱。 例如，假設您的專案含有下列兩個 `Imports` 陳述式：  
  
 [!CODE [VbVbalrApplication#11](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrApplication#11)]  
  
 如果您嘗試使用 `Class1` 但未提供完整名稱，則 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會產生錯誤，表示名稱 `Class1` 模稜兩可。  
  
## 命名空間層級陳述式  
 在命名空間中，您可以定義模組、介面、類別、委派、列舉、結構和其他命名空間等項目。 您無法在命名空間層級定義屬性、程序、變數和事件等項目。 這些項目必須在模組、結構或類別等容器內宣告。  
  
## 完整名稱中的 Global 關鍵字  
 如果您已定義巢狀的命名空間階層，則可能會封鎖該階層內程式碼存取 .NET Framework 的 <xref:System?displayProperty=fullName> 命名空間。 下列範例說明 `SpecialSpace.System` 命名空間會封鎖存取 <xref:System?displayProperty=fullName> 的階層。  
  
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
  
 因此，Visual Basic 編譯器無法順利解析 <xref:System.Int32?displayProperty=fullName> 的參考，因為 `SpecialSpace.System` 未定義 `Int32`。 您可以使用 `Global` 關鍵字，在 .NET Framework 類別庫的最外層啟動限定性鏈結。 這樣做可讓您指定類別庫中的 <xref:System?displayProperty=fullName> 命名空間或任何其他命名空間。 下列範例將說明這點。  
  
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
  
 您可以使用 `Global`，存取其他根層級命名空間 \(例如 <xref:Microsoft.VisualBasic?displayProperty=fullName>\) 和任何與專案相關聯的命名空間。  
  
## Namespace 陳述式中的 Global 關鍵字  
 您也可以在 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)中使用 `Global` 關鍵字。 這可讓您從專案的根命名空間定義一個命名空間。  
  
 專案中的所有命名空間都會以專案的根命名空間為基礎。  Visual Studio 會針對專案中的所有程式碼，將專案名稱指派為預設根命名空間。 例如，如果專案已命名為 `ConsoleApplication1`，其程式設計項目會屬於命名空間 `ConsoleApplication1`。 如果您宣告 `Namespace Magnetosphere`，專案中的 `Magnetosphere` 參考可存取 `ConsoleApplication1.Magnetosphere`。  
  
 下列範例使用 `Global` 關鍵字，從專案的根命名空間宣告一個命名空間。  
  
 [!CODE [VbVbalrApplication#22](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrApplication#22)]  
  
 在命名空間宣告中，`Global` 不能以巢狀方式放在另一個命名空間中。  
  
 您可以使用 [應用程式頁面，專案設計工具 \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic) 來檢視及修改專案的 \[根命名空間\]。  若是新專案，\[根命名空間\] 預設為專案名稱。 若要使 `Global` 成為最上層命名空間，您可以清除 \[根命名空間\] 項目讓方塊空白。 清除 \[根命名空間\] 就不再需要命名空間宣告中的 `Global` 關鍵字。  
  
 如果 `Namespace` 陳述式所宣告的名稱也是 .NET Framework 中的命名空間，當完整名稱中未使用 `Global` 關鍵字時，.NET Framework 命名空間會變成無法使用。 若要允許在不使用 `Global` 關鍵字的情況下存取該 .NET Framework 命名空間，您可以在 `Namespace` 陳述式中包含 `Global` 關鍵字。  
  
 下列範例在 `System.Text` 命名空間宣告中有 `Global` 關鍵字。  
  
 如果 `Global` 關鍵字不在命名空間宣告中，則必須指定 `Global.System.Text.StringBuilder` 才能存取 <xref:System.Text.StringBuilder>。 針對名為 `ConsoleApplication1` 的專案，如果未使用 `Global` 關鍵字，`System.Text` 的參考會存取 `ConsoleApplication1.System.Text`。  
  
 [!CODE [VbVbalrApplication#21](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrApplication#21)]  
  
## 請參閱  
 <xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms?displayProperty=fullName>   
 [組件和全域組件快取](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [如何：使用命令列建立和使用組件](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)   
 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [撰寫 Office 方案中的程式碼](/office-dev/office-dev/writing-code-in-office-solutions)