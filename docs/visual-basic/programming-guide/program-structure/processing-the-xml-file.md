---
title: 處理 XML 檔案
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 81d2c8d305e828b2963a0af9d97ec35b1745197a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398327"
---
# <a name="processing-the-xml-file-visual-basic"></a>處理 XML 檔案 (Visual Basic)
編譯器會針對程式碼中，標記為要產生文件的每個建構產生識別碼字串。 （如需如何標記程式碼的相關資訊，請參閱[XML 註解標記](../../language-reference/xmldoc/index.md)）。識別碼字串可唯一識別結構。 處理 XML 檔案的程式可以使用識別碼字串來識別對應的 .NET Framework 中繼資料/反映專案。  
  
 XML 檔案不是程式碼的階層式標記法;它是包含每個元素所產生之識別碼的一般清單。  
  
 編譯器在產生識別碼字串時會遵守下列規則：  
  
- 字串中未放置任何空白字元。  
  
- 識別碼字串的第一個部分會識別所識別的成員種類，格式為單一字元後面接著一個冒號。 會使用下列成員類型。  
  
|字元|Description|  
|---|---|  
|N|namespace<br /><br /> 您無法將檔批註新增至命名空間，但在支援的情況下，您可以對其進行 CREF 參考。|  
|T|類型： `Class` 、 `Module` 、 `Interface` 、 `Structure` 、 `Enum` 、`Delegate`|  
|F|欄位`Dim`|  
|P|屬性： `Property` （包括預設屬性）|  
|M|方法： `Sub` 、 `Function` 、 `Declare` 、`Operator`|  
|E|發生`Event`|  
|!|錯誤字串<br /><br /> 字串的其餘部分提供與錯誤相關的資訊。 Visual Basic 編譯器會針對無法解析的連結產生錯誤資訊。|  
  
- 的第二個部分 `String` 是專案的完整名稱，從命名空間的根目錄開始。 專案的名稱、其封入類型及命名空間會以句號分隔。 如果專案本身的名稱包含句號，則會以數位記號（#）取代。 假設沒有任何專案直接在其名稱中包含數位記號。 例如，此函式的完整名稱會 `String` 是 `System.String.#ctor` 。  
  
- 針對屬性和方法，如果有方法的引數，則後面會接著以括弧括住的引數清單。 如果沒有任何引數，就不會出現括弧。 引數會以逗號分隔。 每個引數的編碼會直接遵循其在 .NET Framework 簽章中的編碼方式。  
  
## <a name="example"></a>範例  
 下列程式碼顯示如何產生類別及其成員的識別碼字串。  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>另請參閱

- [-doc](../../reference/command-line-compiler/doc.md)
- [如何：建立 XML 文件](how-to-create-xml-documentation.md)
