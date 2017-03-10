---
title: "Errors occurred while compiling the XML schemas in the project | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc36810"
  - "vbc36810"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36810"
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Errors occurred while compiling the XML schemas in the project
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

編譯專案中的 XML 結構描述時發生錯誤。因此，無法使用 XML IntelliSense。  
  
 專案中的 XML 結構描述定義 \(XSD\) 結構描述內發生錯誤。  當您加入與專案現有 XSD 結構描述集衝突的 XSD 結構描述 \(.xsd\) 檔案時，就會發生這個錯誤。  
  
 **錯誤 ID**：BC36810  
  
### 若要更正這個錯誤  
  
-   按兩下 \[**錯誤清單**\] 視窗中的警告。  Visual Basic 會將您帶往屬於警告來源之 XSD 檔案中的位置。  更正 XSD 結構描述中的錯誤。  
  
-   請確定專案中已包含所有必要的 XSD 結構描述 \(.xsd\) 檔案。  您可能必須按一下 \[**專案**\] 功能表上的 \[**顯示所有檔案**\]，查看 \[**方案總管**\] 中的 .xsd 檔案。  以滑鼠右鍵按一下 .xsd 檔案，然後按一下 \[**加入至專案**\]，將該檔案加入專案中。  
  
-   如果您使用 \[XML To Schema 精靈\]，則當您從相同來源多次推斷結構描述時，就會發生這個錯誤。  在這種情況下，您可以從專案中移除現有的 XSD 結構描述檔案，加入新的 XML To Schema 項目樣板 \(Template\)，然後為 \[XML To Schema 精靈\] 提供專案適用的所有 XML 來源。  
  
-   如果 XSD 結構描述中沒有識別任何錯誤，XML 編譯器可能沒有足夠的資訊可提供詳細的錯誤訊息。  如果您確定專案中所包含之 .xsd 檔案的 XML 命名空間符合 Visual Studio 中針對 XML 結構描述集識別的 XML 命名空間，便可以取得更詳細的錯誤資訊。  
  
## 請參閱  
 [錯誤清單視窗](/visual-studio/ide/reference/error-list-window)   
 [XML IntelliSense in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)