---
title: "Processing the XML File (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML comments, parsing [Visual Basic]"
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Processing the XML File (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

編譯器會為每一個加上標記的程式碼的建構產生一個 ID 字串，用來產生文件   \(如需如何標記程式碼的相關資訊，請參閱[XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)\)。 ID 字串會將建構獨一無二地識別出來。  處理 XML 檔案的程式可以使用 ID 字串，識別對應的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 中繼資料 \(Metadata\)\/反映 \(Reflection\) 項目。  
  
 XML 檔案並不代表您程式碼的階層架構，它是一個平面圖式的清單，其中每個項目都有一個 ID。  
  
 在產生 ID 字串時，編譯器會遵守下列的規則：  
  
-   字串中不能有空白。  
  
-   ID 字串的第一個部分 \(單一字元後接著一個分號\) 識別了成員的種類。  下面是使用的成員型別 \(Member Type\)：  
  
|||  
|-|-|  
|字元|描述|  
|N|namespace<br /><br /> 您不能將文件註解加入至命名空間 \(Namespace\)，但是可以產生這些文件註解的 CREF 參考 \(如果有支援這項功能\)。|  
|T|型別：`Class`、`Module`、`Interface`、`Structure`、`Enum`、`Delegate`|  
|F|欄位：`Dim`|  
|P|屬性：`Property` \(包括預設屬性\)|  
|M|方法：`Sub`、`Function`、`Declare`、`Operator`|  
|E|事件：`Event`|  
|\!|錯誤字串<br /><br /> 字串的其餘部分會提供該錯誤的相關資訊。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器對於無法解析的連結會產生錯誤資訊。|  
  
-   `String` 的第二個部分是項目的完整名稱 \(開始於命名空間的根\)。  項目的名稱、其封入型別 \(Enclosing Type\) 和命名空間是以句號分隔的。  若項目的名稱本身含有句號，則句號會被井字號 \(\#\) 所取代。  一般都認定在項目的名稱中沒有井字號 \(\#\)。  例如，`String` 建構函式的完整名稱為 `System.String.#ctor`。  
  
-   對於屬性和方法，若方法有引數，則後面會接著由括號括起來的引數清單。  如果沒有引數，就不會有括弧出現。  引數間是以逗號來分隔。  每個引數的編碼直接遵照 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 簽章中的編碼方式。  
  
## 範例  
 下面程式碼顯示類別 \(Class\) 及其成員的 ID 字串產生方式。  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/processing-the-xml-file_1.vb)]  
  
## 請參閱  
 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)