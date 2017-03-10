---
title: "Type &#39;&lt;typename&gt;&#39; is not defined | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30002"
  - "bc30002"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30002"
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Type &#39;&lt;typename&gt;&#39; is not defined
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

陳述式建立了未定義之型別的參考。  您可以在像是 `Enum`、`Structure`、`Class` 或 `Interface` 的宣告陳述式中定義型別。  
  
 **錯誤 ID：**BC30002  
  
### 若要更正這個錯誤  
  
-   確認型別定義與其參考是否都使用相同的拼字。  
  
-   確認型別定義是否可讓參考存取。  例如，如果型別是在另一模組中且已被宣告為 `Private`，請將型別定義移到參考模組或宣告為 `Public`。  
  
-   確認型別的命名空間是否在專案中已重新定義。  如果已重新定義，請使用 `Global` 關鍵字完整限定型別名稱。  例如，如果專案定義名為 `System` 的命名空間，則除非使用 `Global` 關鍵字加以完整限定，否則無法存取 <xref:System.Object?displayProperty=fullName> 型別：`Global.System.Object`。  
  
-   如果型別已定義，但是定義它的物件程式庫或型別程式庫尚未在 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中註冊，請按一下 \[**專案**\] 功能表的 \[**加入參考**\]，然後選取適當的物件程式庫或型別程式庫。  
  
-   確認型別位在屬於目標 .NET Framework 設定檔一部分的組件中。  如需詳細資訊，請參閱[疑難排解 .NET Framework 目標錯誤](/visual-studio/msbuild/troubleshooting-dotnet-framework-targeting-errors)。  
  
## 請參閱  
 [Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [管理專案中的參考](/visual-studio/ide/managing-references-in-a-project)