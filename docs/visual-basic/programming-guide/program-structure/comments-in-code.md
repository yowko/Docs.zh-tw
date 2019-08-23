---
title: 程式碼中的註解 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
ms.openlocfilehash: 3635d52532789133a345d9a9228efae869c8c223
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945609"
---
# <a name="comments-in-code-visual-basic"></a>程式碼中的註解 (Visual Basic)
當您閱讀程式碼範例時，常會遇到註解符號 (`'`)。 此符號會指示 Visual Basic 編譯器忽略其後面的文字或*批註*。 註解是為了閱讀者方便而加入至程式碼的簡短說明。  
  
 以簡短註解做為所有程序開頭是良好的程式設計作法，此註解會描述程序的基本特性 (作用為何)。 這對於您自己以及對於其他檢查程式碼的人都有好處。 您應該將描述功能特性的註解，與實作 (Implementation) 細節 (程序是如何運作) 分開。 當您將實作細節包含在描述中，請記得在更新函式時，將實作細節一同更新。  
  
 註解可以跟隨在陳述式之後的同一行中，或者佔據一整行。 兩者皆會在以下程式碼中加以說明。  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 如果需要有一行以上的註解，請在每一行中使用註解符號，如下列範例：  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a>註解方針  
 下表提供哪些註解類型可以出現在一段程式碼之前的一般方針。 這些是建議事項;Visual Basic 不會強制執行新增批註的規則。 撰寫對您自己與其他閱讀程式碼的人而言最有效的註解。  
  
|||  
|---|---|  
|註解類型|註解說明|  
|用途|描述程序的功用 (非如何運作)|  
|假設|列出每個外部變數、控制項、開啟檔案或其他程序存取的項目|  
|效果|列出每個受影響的外部變數、控制項或檔案，以及其所受的影響 (僅限於不明顯的)|  
|輸入|指定引數的用途|  
|傳回值|說明程序傳回的值|  
  
 請記住以下要點：  
  
- 每個重要的變數宣告之前都應該有註解，此註解會描述所宣告之變數的用途。  
  
- 變數、控制項和程序應該清楚命名，讓註解只需用於複雜的實作細節中。  
  
- 註解不可以跟隨在同一行的行接續序列之後。  
  
 您可以藉由選取一或多行程式碼, 然後選擇 [**批註**] (![Visual Studio 中的 [Visual Basic 批註] 按鈕) 和 [**取消**批註]](./media/comments-in-code/visual-basic-comment-button.gif)(![視覺效果) 來新增或移除程式碼區塊的批註符號。Visual Studio 中的 [基本取消批註] 按鈕。](./media/comments-in-code/visual-basic-uncomment-button.gif)) 按鈕。  
  
> [!NOTE]
> 您也可以藉由在文字前方置入 `REM` 關鍵字，將註解加入至您的程式碼中。 不過, `'`符號和**批註**/**取消**批註按鈕較容易使用, 而且需要較少的空間和記憶體。  
  
## <a name="see-also"></a>另請參閱

- [基本技術-使用 XML 批註記錄您的程式碼](https://msdn.microsoft.com/magazine/dd722812.aspx)
- [如何：建立 XML 檔](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)
- [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [REM 陳述式](../../../visual-basic/language-reference/statements/rem-statement.md)
