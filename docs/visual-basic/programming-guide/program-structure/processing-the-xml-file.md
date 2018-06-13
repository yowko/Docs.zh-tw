---
title: 處理 XML 檔案 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 6be7597f1c03d8aa044eba70ef6287cfc07d9b84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652034"
---
# <a name="processing-the-xml-file-visual-basic"></a>處理 XML 檔案 (Visual Basic)
編譯器會針對程式碼中，標記為要產生文件的每個建構產生識別碼字串。 (如需如何標記您的程式碼的資訊，請參閱[XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)。)識別碼字串可唯一識別此建構。 處理 XML 檔案的程式可以使用來識別對應的識別碼字串[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]中繼資料/反映項目。  
  
 XML 檔案不是以階層方式呈現您的程式碼;它是以每個項目產生的識別碼為一般清單。  
  
 編譯器在產生識別碼字串時會遵守下列規則：  
  
-   沒有泛空白字元被放在字串中。  
  
-   ID 字串的第一個部分會識別所識別，以單一字元，後面接著冒號成員種類。 會使用下列的成員類型。  
  
|字元|描述|  
|---|---|  
|N|namespace<br /><br /> 您無法將文件註解加入命名空間，但您可以進行 CREF 參考這些有支援。|  
|T|類型： `Class`， `Module`， `Interface`， `Structure`， `Enum`， `Delegate`|  
|F|欄位： `Dim`|  
|P|屬性： `Property` （包括預設屬性）|  
|M|方法： `Sub`， `Function`， `Declare`， `Operator`|  
|E|事件： `Event`|  
|!|錯誤字串<br /><br /> 字串的其餘部分提供與錯誤相關的資訊。 Visual Basic 編譯器會產生無法解析的連結資訊時發生錯誤。|  
  
-   第二個部分`String`是項目，從命名空間的根目錄開始的完整的名稱。 項目、 其封入類型，和命名空間名稱，並以句號分隔。 如果項目本身的名稱包含句點，它們被數字符號 （#）。 它會假設沒有項目，直接在其名稱中有數字的符號。 例如，完整的名稱的`String`建構函式會`System.String.#ctor`。  
  
-   針對屬性和方法，如果有方法的引數，則後面會接著以括弧括住的引數清單。 如果沒有任何引數，就不會出現括弧。 引數會以逗號分隔。 每個引數的編碼方式會遵循直接如何編碼中[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]簽章。  
  
## <a name="example"></a>範例  
 下列程式碼將示範如何的 ID 字串類別，並產生其成員。  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
