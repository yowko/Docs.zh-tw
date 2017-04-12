---
title: "處理 XML 檔案 (Visual Basic) |Microsoft 文件"
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
- XML comments, parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 72b2832d0131adf39a37ebd9297b43fb34ea49ba
ms.lasthandoff: 03/13/2017

---
# <a name="processing-the-xml-file-visual-basic"></a>處理 XML 檔案 (Visual Basic)
編譯器產生的標記來產生文件程式碼中每個建構的識別碼字串。 (有關如何標記程式碼的資訊，請參閱[XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)。)ID 字串可唯一識別此建構。 處理 XML 檔案的程式可以使用識別碼字串來識別對應[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]中繼資料/反映項目。  
  
 XML 檔案不是以階層方式呈現您的程式碼;它是以每個項目產生的識別碼為一般清單。  
  
 產生的識別碼字串時，編譯器會遵守下列規則︰  
  
-   沒有泛空白字元被放在字串中。  
  
-   ID 字串的第一個部分會識別所識別，以單一字元，後面接著冒號成員種類。 使用下列的成員類型。  
  
|字元|描述|  
|---|---|  
|N|namespace<br /><br /> 您無法將文件註解加入至命名空間，但是您可以讓 CREF 參考這些支援。|  
|T|type: `Class`, `Module`, `Interface`, `Structure`, `Enum`,`Delegate`|  
|F|欄位︰`Dim`|  
|P|屬性︰ `Property` （包括預設屬性）|  
|M|method: `Sub`, `Function`, `Declare`,`Operator`|  
|E|事件︰`Event`|  
|!|錯誤字串<br /><br /> 字串的其餘內容提供錯誤的相關資訊。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會產生無法解析的連結資訊時發生錯誤。|  
  
-   第二個部分`String`是開始於命名空間的根項目的完整的名稱。 項目，其封入型別和命名空間名稱，並以句號分隔。 如果項目本身的名稱包含句點，它們被數字符號 （#）。 假設沒有項目，直接在其名稱中有數字的符號。 例如，完整的名稱的`String`建構函式會是`System.String.#ctor`。  
  
-   屬性和方法，如果您有的方法引數括號括住的引數清單如下。 如果不有任何引數，沒有括號會出現。 引數會以逗號分隔。 每個引數的編碼方式會遵循直接如何在編碼[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]簽章。  
  
## <a name="example"></a>範例  
 下列程式碼顯示針對類別 ID 字串的方式，並且會產生其成員。  
  
 [!code-vb[VbVbcnXmlDocComments #&10;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
