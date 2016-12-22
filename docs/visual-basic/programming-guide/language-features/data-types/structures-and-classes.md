---
title: "Structures and Classes (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes [Visual Basic], vs. structures"
  - "structures"
  - "classes [Visual Basic]"
  - "structures, compared to classes"
  - "structures, structure variables"
  - "structure variables"
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Structures and Classes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 之所以將結構與類別的語法統一，是因為兩實體所支援的功能幾乎相同。  不過，結構和類別之間還是有些重大的差異。  
  
 類別具有參考型別 \(Reference Type\) 的好處，那就是傳遞參考要比傳遞結構變數及其所有資料來得有效率。  另一方面，結構不需要配置全域堆積 \(Heap\) 的記憶體。  
  
 由於您無法自結構繼承，因此結構只能使用於不需要擴充的物件。  使用結構的適當時機是，當您要建立之物件的執行個體不大，並且需將類別及結構間效能特性的差異列入考量時。  
  
## 相似點  
 結構和類別在下列幾個方面非常類似：  
  
-   兩者都是「*容器*」\(Container\) 型別，這表示它們包含其他型別做為成員。  
  
-   兩者都有成員，包括建構函式、方法、屬性、欄位、常數、列舉型別、事件和事件處理常式。  但是，請不要將這些成員與結構的宣告「*項目*」\(Element\) 混淆在一起。  
  
-   兩者的成員都有各自的存取層級。  例如，可以宣告一個成員為 `Public`，另一個則可宣告為 `Private`。  
  
-   兩者都可實作介面。  
  
-   兩者都可具有共用建構函式 \(無論是具參數或不具參數都一樣\)。  
  
-   兩者都公開「*預設屬性*」\(Default Property\)，前提是這個屬性至少要有一個參數。  
  
-   兩者都宣告和引發事件，且兩者都宣告委派 \(Delegate\)。  
  
## 差異點  
 結構和類別的差異點如下：  
  
-   結構是「*實值型別*」\(Value Type\)；而類別是「*參考型別*」\(Reference Type\)。  結構型別 \(Structure Type\) 的變數包含有結構的資料，而不是像類別型別包含的是資料的參考。  
  
-   結構使用堆疊配置 \(Stack Allocation\)；而類別使用堆積配置 \(Heap Allocation\)。  
  
-   所有結構項目依預設都是 `Public`；而類別變數和常數依預設是 `Private`，不過其他類別成員依預設都是 `Public`。  類別成員的這種行為提供與 Visual Basic 6.0 預設系統的相容性。  
  
-   結構必須至少擁有一個非共用的變數，或者有非共用的非自訂事件項目；而類別則可以完全是空的。  
  
-   結構項目無法宣告為 `Protected`；而類別成員可以。  
  
-   只有在結構程序是 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` 程序，且只有藉由 [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md)時，結構程序才可以處理事件；而任何類別程序都可以使用 [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) 關鍵字或 `AddHandler` 陳述式處理事件。  如需詳細資訊，請參閱[Events](../../../../visual-basic/programming-guide/language-features/events/events.md)。  
  
-   結構變數宣告無法指定初始設定式或陣列的初始大小；而類別變數宣告則可以。  
  
-   結構是隱含繼承自 <xref:System.ValueType?displayProperty=fullName> 類別而且無法繼承自任何其他型別；而類別則可繼承自 <xref:System.ValueType?displayProperty=fullName> 以外的任何類別。  
  
-   結構是無法繼承的；而類別則相反。  
  
-   結構不會結束，因此 Common Language Runtime \(CLR\) 不會在任何結構上呼叫 <xref:System.Object.Finalize%2A> 方法；而類別則是由記憶體回收行程結束，當記憶體回收行程偵測到沒有剩餘的使用中參考時，它就會在類別上呼叫 <xref:System.Object.Finalize%2A>。  
  
-   結構不需要建構函式；類別需要。  
  
-   結構只能有使用參數的非共用建構函式；類別則可以有具參數或不具參數的非共用建構函式。  
  
 每一個結構都具有無參數的隱含公用建構函式。  這個建構函式會將結構的所有資料項目初始化為其預設值。  您無法重新定義這個行為。  
  
## 執行個體和變數  
 由於結構是實值型別，因此每個結構變數會永久繫結至個別的結構執行個體。  但類別是參考型別，而且物件變數可以在不同時間參考不同的類別執行個體。  兩者之間的區別對於使用結構和類別的影響如下：  
  
-   **初始設定**： 結構變數會隱含包含使用結構的無參數建構函式之項目初始化。  因此，`Dim s As struct1` 就等於 `Dim s As struct1 = New struct1()`。  
  
-   **指派變數**： 當您將一個結構變數指派給另一個，或是將結構執行個體傳遞至程序引數時，所有變數項目的目前值會複製到新的結構中。  當您將一個物件變數指派給另一個，或將物件變數傳遞至程序時，則只會複製參考指標。  
  
-   **指派 Nothing**： 您可將 [Nothing](../../../../visual-basic/language-reference/nothing.md) 值指派給結構變數，但執行個體會持續保持與變數的關聯。  雖然變數項目會因指派而重新初始化，但您還是可以呼叫變數的方法並存取其資料項目。  
  
     相反地，如果將物件變數設定為 `Nothing`，就會中斷它與任何類別執行個體的關聯，而且除非再將另一個執行個體指派給它，否則無法透過變數存取任何成員。  
  
-   **多個執行個體**： 物件變數在不同時間可有不同的指派類別執行個體，而且數個物件變數可同時參考同樣的類別執行個體。  當透過指向相同執行個體的其他變數來存取時，您對類別成員值所作的變更會影響這些成員。  
  
     不過，結構項目在本身執行個體內是隔離的。  變更它們的值並不會對任何其他結構變數造成影響，甚至也不會影響相同 `Structure` 宣告的其他執行個體。  
  
-   **相等**： 兩個結構必須以項目對項目測試的方式執行相等測試。  兩個物件變數可以使用 <xref:System.Object.Equals%2A> 方法進行比較。  <xref:System.Object.Equals%2A> 會指示兩個變數是否指向相同的執行個體。  
  
## 請參閱  
 [資料類型](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Objects and Classes](../../../../visual-basic/reference/command-line-compiler/index.md)