---
title: "結構和類別 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures
- classes [Visual Basic]
- structures, compared to classes
- structures, structure variables
- structure variables
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: 21
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: e7402ec0fcfc279470d39a4919d3b5ec8b5d9dff
ms.lasthandoff: 03/13/2017

---
# <a name="structures-and-classes-visual-basic"></a>結構和類別 (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]統一的語法結構和類別，因為這兩個實體支援的大部分相同的功能。 不過，還有結構和類別間的差異。  
  
 類別具有的優點是參考型別，傳遞參考會比將它的資料結構變數傳遞更有效率。 相反地，結構不需要全域堆積上的記憶體配置。  
  
 您無法從結構繼承，因為結構應該僅適用於不需要擴充的物件。 當您想要建立的物件有小型執行個體的大小，並納入類別與結構的效能特性，請使用結構。  
  
## <a name="similarities"></a>相似之處  
 結構和類別是在下列方面類似︰  
  
-   兩者都是*容器*型別，也就是說它們包含做為成員的其他類型。  
  
-   兩者都有成員，可以包含建構函式、 方法、 屬性、 欄位、 常數、 列舉型別、 事件和事件處理常式。 不過，請勿混淆與宣告這些成員*項目*的結構。  
  
-   兩者的成員都有各自的存取層級。 例如，可以宣告一個成員`Public`，另一個`Private`。  
  
-   兩者都可以實作介面。  
  
-   兩者都可以有共用的建構函式參數。  
  
-   兩者都可以公開*預設屬性*，可提供屬性採用一個以上的參數。  
  
-   兩者都可以宣告和引發事件，而且兩者都可以宣告委派。  
  
## <a name="differences"></a>差異  
 結構和類別，差異如下︰  
  
-   結構是*實值型別的*; 類別是*參考型別*。 結構類型的變數包含結構的資料，而不是未包含的資料做為類別類型的參考。  
  
-   結構會使用堆疊配置。類別會使用堆積配置。  
  
-   所有的結構項目都`Public`依預設，類別變數和常數是`Private`根據預設，其他類別成員時`Public`預設。 類別成員的這個行為可提供與 Visual Basic 6.0 系統的預設值的相容性。  
  
-   結構必須至少一個非共用變數或非共用、 非自訂事件項目。類別可以完全空白。  
  
-   結構項目不能宣告為`Protected`; 可以類別成員。  
  
-   結構的程序可以處理事件，才[共用](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub`程序，並只透過的方式來[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md); 類別中的任何程序可以處理事件，使用[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)關鍵字或`AddHandler`陳述式。 如需詳細資訊，請參閱[事件](../../../../visual-basic/programming-guide/language-features/events/index.md)。  
  
-   結構變數宣告不能指定初始設定式或初始陣列的大小。可以類別變數的宣告。  
  
-   結構隱含繼承自<xref:System.ValueType?displayProperty=fullName>類別，並與任何其他類型; 無法繼承類別可以繼承自任何類別或類別以外<xref:System.ValueType?displayProperty=fullName>.</xref:System.ValueType?displayProperty=fullName> </xref:System.ValueType?displayProperty=fullName>  
  
-   結構是無法繼承。類別是。  
  
-   結構會永遠不會終止，因此 common language runtime (CLR) 永遠不會呼叫<xref:System.Object.Finalize%2A>方法上的任何結構; 類別會由記憶體回收行程 (GC)，它會呼叫終止<xref:System.Object.Finalize%2A>上時偵測到沒有剩餘的作用中參考的類別。</xref:System.Object.Finalize%2A> </xref:System.Object.Finalize%2A>  
  
-   結構不需要建構函式。類別會執行。  
  
-   結構可以具有非共用的建構函式才會顯示參數。類別可以讓他們無論有參數。  
  
 每個結構具有不含參數的隱含公用建構函式。 這個建構函式會初始化成為其預設值結構的所有資料項目。 您無法重新定義此行為。  
  
## <a name="instances-and-variables"></a>執行個體和變數  
 結構是實值型別，因為每個結構變數會永久繫結到個別的結構執行個體。 但類別是參考型別，而且物件變數可以參考各種類別執行個體在不同的時間。 這項區別會以下列方式影響結構和類別的使用方式︰  
  
-   **初始化。** 結構變數隱含地包含使用結構的無參數建構函式的元素初始化。 因此，`Dim s As struct1`相當於`Dim s As struct1 = New struct1()`。  
  
-   **指派變數。** 當您將一個結構變數指派給另一個，或將結構執行個體傳遞至程序引數時，目前的值的所有變數的項目會複製到新的結構。 當您將一個物件變數指派給另一個，或將物件變數傳遞至程序時，只會複製參考指標。  
  
-   **指派執行任何動作。** 您可以將值指派[Nothing](../../../../visual-basic/language-reference/nothing.md)結構變數，但執行個體仍可繼續與變數相關聯。 您仍可以呼叫其方法及存取資料元素，但藉由指派的變數項目都會重新初始化。  
  
     相反地，如果您將物件變數設定為`Nothing`中斷關聯從任何類別執行個體，您無法透過變數存取任何成員，直到您指派給它的另一個執行個體。  
  
-   **多個執行個體。** 物件變數可以有不同的類別執行個體指派給不同的時間和數個物件變數可以參考相同的類別執行個體在相同的時間。 您對類別成員的值的變更會影響當透過指向相同的執行個體的另一個變數來存取這些成員。  
  
     不過，結構項目，是放在自己的執行個體。 其值的變更不會反映在任何其他結構變數，即使是在相同的其他執行個體`Structure`宣告。  
  
-   **相等。** 必須與項目依項目測試執行的兩個結構相等測試。 可以使用比較兩個物件變數<xref:System.Object.Equals%2A>方法。</xref:System.Object.Equals%2A> <xref:System.Object.Equals%2A>表示兩個變數是否指向相同的執行個體。</xref:System.Object.Equals%2A>  
  
## <a name="see-also"></a>另請參閱  
 [資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [複合資料型別](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [結構和其他程式設計項目](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
