---
title: "Static (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Static"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "static modifier"
  - "Static keyword"
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Static (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定一個或多個宣告的區域變數會繼續存在，並在宣告它們的程序終止之後保持其最新的值。  
  
## 備註  
 通常，一旦程序停止後，程序中的區域變數就不復存在，  而靜態變數會繼續存在並保留其最新值。  下次當程式碼呼叫程序時，不會重新初始化變數，而且它仍會保存您指派給它的最新值。  只要在其中定義靜態變數的類別或模組存在，靜態變數就會繼續存在。  
  
## 規則  
  
-   **宣告內容：**您只能在區域變數上使用 `Static`。  這表示 `Static` 變數的宣告內容必須是程序或程序內的區塊，而且它不能是原始程式檔 \(Source File\)、命名空間、類別、結構或模組。  
  
     您不可在結構程序內使用 `Static`。  
  
-   無法推斷 `Static` 區域變數的資料型別。  如需詳細資訊，請參閱[Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
-   **組合的修飾詞：**您無法在同一個宣告中同時指定 `Static` 與 `ReadOnly`、`Shadows` 或 `Shared`。  
  
## 行為  
 當您宣告中的靜態變數`Shared`程序中，此靜態變數只有一個複本適用於整個應用程式。  您呼叫`Shared`程序，使用類別名稱、 非指向類別的執行個體變數。  
  
 當您宣告靜態變數中的程序不是`Shared`，只有一個變數的複本可用每個執行個體的類別。  您可以使用此變數會指向特定類別的執行個體，以呼叫非共用的程序。  
  
## 範例  
 以下範例將說明 `Static` 的用法。  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/visualbasic/static_1.vb)]  
  
 `Static` 變數 `totalSales` 只會初始化為 0 一次。  每次輸入 `updateSales` 時，`totalSales` 仍具有您為它計算的最新值。  
  
 `Static` 修飾詞可用於以下內容中：  
  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## 請參閱  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Lifetime in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)